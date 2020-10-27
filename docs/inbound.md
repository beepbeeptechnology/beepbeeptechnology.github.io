# Inbound Data Automation
The first step is determining where your data is and how you are going to get it into BigQuery.  The approach depends on a number of factors, and you have a lot of options with varying degrees of up-front effort and ongoing maintenance and monitoring requirements.

=== "BigQuery Hosted"
    If you are lucky enough then the data you need is already in BigQuery, and you don't need to do any inbound automation at all.  This is great news.

    === "Public Datasets"
        [BigQuery Public Datasets](https://cloud.google.com/public-datasets) are datasets which are hosted and maintained for free on BigQuery where you only pay query costs.  You can explore these datasets through the BigQuery UI by browsing to the [bigquery-public-datasets](https://console.cloud.google.com/bigquery?project=bigquery-public-data) project.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle-half-full: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle-outline: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        
    === "Commercial Datasets"
        [BigQuery Commercial Datasets](https://console.cloud.google.com/marketplace/browse?filter=solution-type:dataset&hl=vi) are datasets which are hosted on BigQuery, but require you to enter into a commercial arrangement with the provider.  Available datasets can be explored on the [Google Cloud Marketplace](https://console.cloud.google.com/marketplace) by filtering for datasets.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle-half-full: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle-half-full: :material-circle-outline: :material-circle-outline: :material-circle-outline:|

=== "Google Managed Transfer"
    The next best option is to let Google manage the transfer of data into BigQuery, which gives you two different mechanisms depending on the data source.

    === "Data Transfer Service"
        If your data source is supported by the [BigQuery Data Transfer Service](https://cloud.google.com/bigquery-transfer/docs/introduction), then you can configure a periodic transfer which is managed by Google.  This includes a lot of Google data sources and Amazon S3 buckets, however with some limitations.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        
    === "Transfer Service for Cloud Data"
        If your data is in an external storage bucket (i.e. Amazon S3 or Azure Storage Container) then you can use this service to transfer files (with more complex filtering functionality) to a Google Cloud Storage bucket and query this directly from BigQuery.

        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle-half-full: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
        
=== "Third Party Services"
    There are a huge number of third-party services broadly known as ETL (Extract-Transform-Load) tools which will take care of managing your inbound data automation.  These tools are constantly evolving, expanding and being acquired so we give a brief overview here which is accurate at the time of writing.  The tool(s) you select will depend on the data sources which they support, which is always expanding.
    There is also another category of services which specialise in analysing customer behaviour, which will typically send data directly into BigQuery.

    === "Recommended ETL Tools"
        We have had extensive exposure to these tools and deployed them to live data pipelines with a high level of success.  As such we are comfortable setting up these tools on behalf of our clients, and either providing training to enable self-monitoring, or monitoring these services on their behalf.

        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:|
     
        === "Stitch Data"
            [Stitch Data](https://www.stitchdata.com/) is a simple to set up, reliable and highly recommended option based on the [Singer](https://www.singer.io/) open standard.  Unfortunately the previous generaous free tier has now been '[sunsetted](https://www.stitchdata.com/blog/free-plan-sunset/)'.
        
        === "Supermetrics"
            [Supermetrics](https://supermetrics.com/) is a marketing-focused service which can reliably push your data to a number of different places including BigQuery or direct into Google Data Studio. It also integrates natively with the Google Data Transfer Service (new options show up once you are signed up to the service)
            
        === "Rivery"
            [Rivery](https://rivery.io/) is a highly recommended service, with a huge number of additional capabilities and great monitoring tools.  They will also build custom API integrations for a fee. 
            
        === "Skyvia"
            [Skyvia](https://skyvia.com/) is a service we have used with success as it offers some interesting integrations and customisation functionality.
 
        === "Data.World"
            [Data.World](https://data.world/) is a little different as it is technically a data catalog, but it has some interesting capabilities regarding inbound data automation and chart building.  
        
        === "Meltano"
            [Meltano](https://meltano.com/) is actually an end-to-end open-source solution for more technically-minded people, developed by GitLab.  It works by managing data transfer using Singer taps/targets, with DBT for data transformation and Apache Airflow for orchestration.
    
    === "Customer Analytics"
        This set of services worth mentioning, as they give you the capability to track user behaviours across your website(s) and/or app(s).  They require some technical knowledge to set up and manage, which is beyond the scope of our core services.  However we are experienced at working with the data which they generate and push directly to BigQuery.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:|     

        * [Segment](https://segment.com/)
        * [Mixpanel](https://mixpanel.com/)
        * [Heap](https://heap.io/)
    
    === "Other ETL Tools"
        There are a large number of other ETL tools out there, to which we have had limited - if any - exposure.  These might suit your integration and/or budget requirements, but we do not have experience setting up or using the tools in a live environment.  However, we are comfortable working with the data generated and sent to BigQuery.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:|        
    
        * [Fivetran](https://fivetran.com/)
        * [Blendo](https://www.blendo.co/)
        * [Hevo Data](https://hevodata.com/)
        * [XPlenty](https://www.xplenty.com/)
        * [Alooma](https://www.alooma.com/) (acquired by Google)
        
=== "External Files"
    We can automate the flow of data from files which are hosted publicly (open to anybody on the internet) or privately (behind a login or authentication mechanism).
          
    Complexity is driven by whether the URL and or filename is stable and consistent, and also whether the whole dataset is contained in the file or whether the data needs to be appended to the destination dataset. 
 
    For robustness, our recommended approach is to periodically load the hosted data into our Cloud Storage, and build logic in the downstream pipeline to ensure that the destination dataset contains the correct and most recent data available.
        
    File types are typically CSV or JSON format.  However we can also process Avro and Parquet files using existing processes, and potentailly additional file types upon request.
    
    === "Public Data"
        In order to automate this process from a public website (e.g. a public GitHub respository) we use our own serverless architecture to periodically check for file changes and load new data when it becomes available.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline: |
        | Ongoing Effort | :material-circle: :material-circle-half-full: :material-circle-outline: :material-circle-outline:| 

    === "Private Data"
        Accessing private data in external files is similar to accessing public data, and we apply the same checks for file change detection.  However there is an additional layer of complexity as the request will need authentication credentials to access the data.
        
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle-half-full: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:|     

=== "External APIs"
    A more complex but flexible and powerful source of data is via external APIs (Application Programming Interfaces), to which we send requests to periodically extract data, which we then manage and push to the downstream data pipeline.  
    
    Complexity is driven by potentially changing response schemas and the need to orchestrate the requests so that no data is missed, changed data is updated and replicated data is de-duplicated downstream.
    
    We manage our custom API data sources using Serverless [Cloud Functions](https://cloud.google.com/functions/) in Python.  Development of these  is made more straightforward if there is a comprehensive client library.
    
    There is more significant development and management effort associated with custom API data sources, so we would advise you to use a third-party service if available.  However, we are extremely experienced at API interaction so can build integrations and manage ongoing infrastructure for you if required as part of our core services. 
       
    === "Public API"
        Public APIs are the most straightforward to work with as there is no authentication mechanism, however there is still a base level of effort required to investigate, test, build and deploy any API data source.
    
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle: :material-circle-outline:|
        | Ongoing Effort | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:|
         
    === "Authenticated API"
        Authenticated APIs add an additionalty layer of complexity (and potential common point of failure) as the requests need to be authenticated before the API will send a response.  As such there is additional initial effort and ongoing management.

        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle: :material-circle-half-full:|
        | Ongoing Effort | :material-circle: :material-circle: :material-circle-half-full: :material-circle-outline:|
    
    === "Multi-Tenant"
        For some use cases you might need to access similar data sources for multiple clients, which comes with an even higher level of complexity due to more complex authntication processes (e.g. OAuth).  Effort for these needs to be assessed on a case-by-case basis, but is generally high.
    
        | Automation Effort | Level |
        | -- | -- |
        | Initial Effort | :material-circle: :material-circle: :material-circle: :material-circle:|
        | Ongoing Effort | :material-circle: :material-circle: :material-circle: :material-circle-outline:|