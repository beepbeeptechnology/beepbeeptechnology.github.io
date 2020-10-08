# Data Transformation
Once your data is loaded into BigQuery, If your inbound data is structured, named and integrated in exactly the way you need to consume it, then that's awesome news!  You can skip most of these steps, however you should still profile the data to ensure that it is free of e.g. duplicate rows or meaningless columns.

## Data Profiling
Before undertaking any data transformation, it is important to profile the incoming data to understand the overall shape (schema, row count) and data types.  Subsequently, investigation of the actual data is advisable to identify if the data contains duplicates, unexpected gaps, data type discontinuities or other characteristics which flag issues to address.

It is also often extremely valuable to understand more nuanced characteristics of the data, from basic statistics (mean, median, mode), to understanding column cardinality, distribution and correlations between columns.

## Transformation Types

We think about data transformations in terms of the following categories, with a range of different objectives and corresponding approaches.

=== "Cleanse"
    Data cleanse activities automate the 'correction' of data, whether that is filtering out duplicate rows, cleaning unwanted characters from strings which can cause downstream errors.  Cleanse activities can use native functionality and/or some more custom functions.
    
=== "Convert"
    To leverage the full capabilities of BigQuery, it is important to ensure that data types are correct, which can be complex depending on the precise format the data is received in.  Date and time formats can pose particular challenges, as well as differing national standards.
    
=== "Filter"
    Common transformation actions are to filter down unwanted or unused columns from the data - improving downstream performance - or to filter down the dataset based on a column values combination of column values, expose a subset of the data to downstream tools.

=== "Aggregate"
    [Aggregate functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/aggregate_functions) then perform some kind of aggregation on the date, grouping the date by a set of dimensions and executing a computation on the rows which correspond to the dimension set.  Example functions are `MIN`, `MAX`, `SUM` or `COUNT` and normally result in a different (lower) output row count.

=== "Compute"
    Computation functions are more complex and are often based on [Analytic Functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts), and can achieve complex computational outputs in a single step such as row occurrence counts, or encapsulated in datafunctions to quickly compute e.g. grouped moving averages.
    
=== "Transform"
    Transform functions fundamentally reshape the data, which may be desirable for downstream purposes.  These functions perform actions like pivotting data to transform tidy data into a set of dimensions and columns containing statistics, or unpivotting to achieve the inverse transform.
    
=== "Integrate"
    You will almost certainly want to integrate your data with data from other sources. In SQL, this typically means a type of JOIN, which connects data on a shared set of dimensions.  It is critical to profile pre- and post-join datasets as it is very easy to unwittingly duplicate rows or lose data.

## Transformation Options
If your data needs to be cleansed, transformed or integrated with other data, you have some options for how you can do this.

=== "SQL"
    BigQuery uses Standard SQL (Structured Query Language) for all data manipulation, which is a SQL dialect with some powerful additional capabilities. Simple transformation steps can be written as Standard SQL views, which can then be queried directly from your downstream tools.

=== "datafunctions"
    For more complex and/or repetitive transformation requirements it can be extremely painful and time-consuming to hand-write SQL.  In these instances, we leverage dynamic SQL in BigQuery.  This enables common SQL patterns to be abstracted into re-useable functions ([User Defined Functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/user-defined-functions) and [Stored Procedures](https://cloud.google.com/bigquery/docs/reference/standard-sql/scripting)) which can be chained together to build complex, reuseable transformation patterns.
    
    Underpinning this approach is a library of functions which we build and maintain called datafunctions ([datafunctions.github.io](https://datafunctions.github.io)), which are callable directly in BigQuery using the syntax `datafunctions.functiontype.function([ARGUMENTS])`.
   
=== "Third Party Platforms"
    There are some excellent platforms which bring software engineering best practices to the data engineering workflow, and which might be applicable to your use case.  As external tools there will be some onboarding effort and a learning curve as well as ongoing maintenance effort and potential cost.  However these tools are worth consideration.

    === "dbt" 
        Data Build Tool ([dbt](https://www.getdbt.com/)) is a open source platform with a hosted paid option, which allows anyone comfortable with SQL to own the data transformation work that happens between loading data into your warehouse and analyzing it.  It is written in Python and includes advanced templating using Jinja, version-controlled automated documentation, testing, package management and a huge amount of additional functionality.
        
    === "DataForm"
        [DataForm](https://dataform.co/) is another highly regarded modern analytics engineering platform, with a very similar objective to dbt, and a focus on collaboration between data teams and a unified, robust approach to data modelling.  Whereas dbt is Python-centric, DataForm leverages JavaScript, so your choice of tool might be influenced by team capabilities in these languages.
    
    
=== "ETL Tools"
    Some ETL tools enable you to do data transformations to a varying degree before you load the data into BigQuery.  However our preferred approach is to separate logical activities and use ETL tools to load the data in the original form (with maybe an additional load timestamp or other load metadata), transform in BigQuery, and then give your external tools access to the transformed dataset.  This gives the additional benefit of making it simpler to swap out pipeline components with minimal additional effort, avoiding being 'locked in' to specific providers.
    
    
=== "Downstream Tools"
    You can also undertake transformations within your downstream tools, which might seem easier at the time, but which can cause longer term issues.  Building complex logic into e.g. a spreadsheet or your Business Intelligence tool can be very difficult to quality assure, replicate or scale.  Building all of your transformation logic into BigQuery enables you to avoid these potential pitfalls, as well as eliminating 'lock in' to a specific tool, and ensuring that every tool you use to access your data has the same, single source of truth.
