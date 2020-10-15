# Outbound Data Automation
Transformed data is made available for downstream tools and services as [BigQuery views](https://cloud.google.com/bigquery/docs/views-intro) (dynamic data which will auto-refresh when queried) and/or [BigQuery tables](https://cloud.google.com/bigquery/docs/tables-intro) (periodically refreshed and typically faster to query).  

The tool you want to use to connect to your data should have a native BigQuery connector.  If it doesn't then you can optionally:

1. Use a different tool
1. Get the company which provides the tool to build a connector
1. Build (or pay a developer to build) a custom connector
1. Find a workaround (via e.g. Google Sheets)

We typically advise option 1 (use a tool with a native connector) as all other options incur varying degrees of additional up-front cost and/or ongoing monitoring and maintenance, with higher potential for failure in the future. 

## Data Destinations
Of course, setting up your inbound data automation and fine-tuning your transformation pipelines to build beautiful and bomb-proof data pipelines is a total waste of time unless you actually do something with the data!  The categories of tools which need to be connected to your data in BigQuery are typically:

=== "BI Tools"
    BI (Business Intelligence) tools are a fairly broad category, with a broad range of feature sets, complexity, prices, modernity and hosting options, but fundamentally aligned around translating data into visual representations to help find insights.  We present a few options we have had experience with, none of which is perfect but all have positive reasons to consider them.
    
    === "Google Data Studio"
        [Google Data Studio](https://datastudio.google.com/) is our go-to BI tool.  It is far from perfect and has its own quirks, but it is completely free, has a rock-solid integration with BigQuery and is improving in functionality at a rapid pace.  It's fully cloud-based, sharing and access control is simple via the usual Google mechanisms, and you can schedule email reports to go out periodically.
        
        Connection to BigQuery is very simple, robust and outlined [here](https://support.google.com/datastudio/answer/6370296?hl=en).
        
    === "Tableau"
        [Tableau](https://www.tableau.com/) was a trailblazer in this space, but the veteran is - in our opinion at least - looking a little more dinosaur-like in this cloud native world.  It is at its core a very powerful desktop application, with options to publish workbooks and data sources publicly or privately. Licensing model can get expensive, a steep learning curve and complex to quality assure dashboards.
        
        Connection to BigQuery is simple (outlined [here](https://help.tableau.com/current/pro/desktop/en-us/examples_googlebigquery.htm)), but you need to be careful of data type errors.
        
    === "Looker"
        [Looker](https://looker.com/) has always been a highly capable tool which is however prohibitively expensive for most startups and small organisations.  Acquired by Google, it will be interesting to see if this means any more affordable options will emerge.  Pioneer in data modelling/transformation, undoubtable powerful but locks you into their vendor-specific LookML view of the world.
        
        Connection to BigQuery requires creation of a service account in GCP, outlined [here](https://docs.looker.com/setup-and-management/database-config/google-bigquery).
        
    === "Mode"
        [Mode Analytics](https://mode.com/) is a slightly different beast, as it integrates Python, R and data visualisation into a modern SQL-based UI. Fully cloud-based and very intuitive interface, however the licensing model is very opaque and can (apparently) be quite expensive.  As an aside, they have an amazing, comprehensive and free [SQL tutorial](https://mode.com/sql-tutorial/) we frequently reference for foundational concepts.
        
        Connection to BigQuery requires creation of a service account in GCP, outlined [here](https://mode.com/help/articles/bigquery/).
                
    === "Microsoft Power BI"
        [Power BI](https://powerbi.microsoft.com/) is a good option if you are already bought into the Microsoft ecosystem as it is apparently a powerful and affordable BI tool with good integration the rest of the Microsoft tools.
        
        Connection is fairly straightforward (outlined [here](https://docs.microsoft.com/en-us/power-bi/connect-data/desktop-connect-bigquery)).
        
    === "Vega Lite"
        [Vega Lite](https://vega.github.io/vega-lite/) isn't technically a BI tool, rather a high-level grammar of interactive graphics used in a large and growing number of tools.  Charts are specified in JSON, interactive and highly portable (even embeddable in Data Studio), and the Python library [Altair](https://altair-viz.github.io/) is one of the best. There is also an excellent GUI based [Chart Builder](https://data.world/integrations/dw-chart-builder) in [data.world](https://data.world/) which connects to BigQuery.
        
        Connection from BigQuery to data.world is via a service account, outlined [here](https://data.world/integrations/bigquery).
        
=== "Spreadsheet Applications"
    Spreadsheets are the tools in which analysts have historically done most of their data work, and they are so flexible that they can be used for pretty much any conceivable purpose.  Which is the problem.  In our opinion, spreadsheets are extremely useful for hacking around with data for quick and dirty data discovery, however when used as part of a workflow they can rapidly get out of hand.  Processes built around spreadsheets don't scale well and are prone to undetected errors.  
    
    Cloud hosted spreadsheets have taken away complexity around version control, but they still represent a risky point of failure and introduce human error, as well as 'helpful' automatic actions like dropping zeroes from the front of telephone numbers or changing all of your perfect ISO compliant dates into integers.
    
    === "Google Sheets"
        Google Sheets has very good integrations with BigQuery, which can be extremely helpful.  You can query data in a Google Sheet [directly from BigQuery](https://cloud.google.com/bigquery/external-data-drive), and changes are reflected immediately when queried.  You can also send data back the other way using [Connected Sheets](https://cloud.google.com/bigquery/docs/connected-sheets), and schedule extracts into your workbooks.  This requires a GSuite for Business account.  However, regarding this workflow: moving data through a spreadsheet can seem like a good idea until it breaks and you have no debugging framework, or any idea where to start trying to fix it.
        
    === "Microsoft Excel"
        MIcrosoft Excel _can_ connect to BigQuery, but setup is not trivial.  You need to install the [Magnitude Simba ODBC driver for BigQuery](https://cloud.google.com/bigquery/providers/simba-drivers), which apparently works on Windows, Linux and MacOS.  We have been able to get the connector working on Windows, however if you do need this workflow, then it might be worth thinking about your end-to-end workflow and whether it's still fit-for-purpose given the technical tools and resources we now have at our disposal. 
    
    === "Lotus 1-2-3"
        Ha ha only joking! One from the [history books](https://en.wikipedia.org/wiki/Lotus_1-2-3)...

=== "Cloud Storage"
    It is a fairly common data exchange pattern to be required to send data files to a cloud storage location for a partner/client/customer to process downstream.  We can set up the mechanism to automate this export to a range of common cloud destinations. 

    === "Google Cloud Storage"
        Google Cloud Storage buckets are used for inbound data and can also be used as a location to periodically export data depending on specific requirements.  
        
    === "Amazon S3"
        Amazon S3 buckets can also be used as a location to periodically export data depending on specific requirements.  This would require additional Amazon authentication details. 
         
    === "Azure Storage"
        Microsoft Azure Storage Locations can also be used as a location to periodically export data depending on requirements. This would require additional Microsoft authentication details. 
                
    === "Google Drive"
        Files can also be periodically exported to a Google Drive location periodically, depending on the specific requirements.
        
    === "Dropbox"
        Files can also be periodically exported to a Dropbox directory  periodically, depending on the specific requirements.
        
=== "Programmatic Access"
    BigQuery has Google-developed and supported client libraries for all major languages, which make interacting with your dataset programmatically very straightforward.  Authentication processes vary, but consistently require you to create a service account, add the required permissions, download the key (JSON file) and then use the path to the key file in your code. 

    === "Cloud Functions"
        Cloud Functions are serverless, event-driven functions which can be triggered via a variety of secure mechanisms.  They can be written in Node.js, Python, Go or Java, so programmatic access is via the Client Library for the relevant language.  
        
    === "Python"
        We have used the [Python Client Library](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-python) extensively and find it simple and robust.
        
    === "Node.js"
        Documentation on how to set up the Node.js Client Library is available [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-nodejs).
        
    === "Go"
        Documentation on how to set up the Go Client Library is available [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-go).
        
    === "Java"
         Documentation on how to set up the Java Client Library is available [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-java).   
    
    === "Ruby"
         Documentation on how to set up the Ruby Client Library is available [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-ruby).
             
    === "C#"
         Documentation on how to set up the C# Client Library is available [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-ruby).        
    
    === "PHP"
        Please don't.  But if you must, the documentation is [here](https://cloud.google.com/bigquery/docs/reference/libraries#client-libraries-install-php).        


=== "Attachments"
    There are also use-cases where partners/clients/customers require data files to be sent periodically as attachments for downstream processing.  We can set up the mechanism to automate this via a variety of channels.
    
    === "Email"
        Email is probably the most common use case, but does involve some setup complexity to ensure that the emails are correctly authorised and not identified as spam.
        
    === "Slack"
        Slack is a more straightforward process to set up, requiring some basic authentication details for attachments to be periodically attached to messages in a specific channel.