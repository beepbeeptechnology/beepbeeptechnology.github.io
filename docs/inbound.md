# Inbound Data Automation
The first step is determining where your data is and how you are going to get it into BigQuery.  The approach depends on a number of factors, and you have a lot of options with varying degrees of up-front effort and ongoing maintenance and monitoring requirements.

=== "BigQuery Hosted"
    If you are lucky enough then the data you need is already in BigQuery, and you don't need to do any inbound automation at all.  This is great news.

    === "Public Datasets"
        [BigQuery Public Datasets](https://cloud.google.com/public-datasets) are datasets which are hosted and maintained for free on BigQuery.  You only pay to query, but some of the datasets are significant in size so be wary of this.  You can explore these datasets through the BigQuery UI bu browsing to the [bigquery-public-datasets](https://console.cloud.google.com/bigquery?project=bigquery-public-data) project.
    === "Commercial Datasets"
        [BigQuery Commercial Datasets](https://console.cloud.google.com/marketplace/browse?filter=solution-type:dataset&hl=vi) are datasets which are hosted on BigQuery, but require you to enter into a commercial arrangement with the provider.

=== "Google Managed Transfer"
    The next best option is to let Google manage the transfer of data into BigQuery, which gives you two different mechanisms depending on the data source.

    === "Data Transfer Service"
        If your data source is supported by the [BigQuery Data Transfer Service](https://cloud.google.com/bigquery-transfer/docs/introduction), then you can configure a periodic transfer which is managed by Google and very robust.  This includes a lot of Google data sources (e.g. Google Analytics, Google Play, YouTube) and does include Amazon S3 buckets as a source, however with some limitations.
    
    === "Transfer Service for Cloud Data"
        If your data is in an external storage bucket (i.e. Amazon S3 or Azure Storage Container) then you can use this service to transfer files (with more complex filtering functionality) to a Google Cloud Storage bucket and query this directly from BigQuery.

        
=== "Third Party Services"
    There are a huge number of third-party services broadly known as ETL (Extract-Transform-Load) tools which will take care of managing your inbound data automation.  These tools are constantly evolving, expanding and being acquired so we give a brief overview here which is accurate at the time of writing.  The tool(s) you select will depend on the data sources which they support, which is always expanding 
    There is also another category of services which specialise in  

    === "Recommended ETL Tools"
        We have had extensive exposure to these tools and deployed them to live data pipelines with a high level of success.  As such we are comfortable setting up and/or managing these tools on behalf of our clients.
        
        === "Stitch Data"
            [Stitch Data](https://www.stitchdata.com/) is a simple to set up, reliable and highly recommended option based on the [Singer](https://www.singer.io/) open standard.  It has a generous free tier.
        === "Supermetrics"
            [Supermetrics](https://supermetrics.com/) is a marketing-focused service which can reliably push your data to a number of different places including BigQuery or direct into Google Data Studio. It also integrates natively with the Google Data Transfer Service (new options show up once you are signed up to the service)
            
        === "Rivery"
            [Rivery](https://rivery.io/) is a highly recommended service, with a huge number of additional capabilities and great monitoring tools.  They will also build custom API integrations for a fee. 
            
        === "Skyvia"
            [Skyvia](https://skyvia.com/) is a service we have used with success as it offers some interesting integrations and customisation functionality.
 
        === "Data.World"
            [Data.World](https://data.world/) is a little different as it is technically a data catalog, but it has some interesting capabilities regarding inbound data automation, chart building and.  
    
    
    === "Customer Analytics"
        There is also a set of services worth mentioning, which give you the capability to track user behaviours across your website(s) and/or app(s).  They require some technical knowledge to set up and manage, which is beyond the scope of our services.  However we are experienced at working with the data which they generate and push directly to BigQuery.
        
        * [Segment](https://segment.com/)
        * [Mixpanel](https://mixpanel.com/)
        * [Heap](https://heap.io/)
       
    === "Other ETL Tools"
        There are a large number of other ETL tools out there, to which we have had limited - if any - exposure.  These might suit your integration and/or budget requirements, but we do not have experience setting up or using the tools in a live environment.  However, we are comfortable working with the 
         
        * Fivetran
        * Hevo Data
        * XPlenty
        * Blendo
        * Alooma (acquired by Google)
        * Talend (acquired Stitch Data)
        

=== "External Files"

    === "Public Data"
    === "Private Data"


=== "External APIs"
    
    === "Public Data"
    === "Private Data"
    === "Multi-Tenant"