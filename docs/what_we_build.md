# What We Build
We build and monitor serverless, automated data pipelines on Google Cloud Platform, enabling you to rely on your data being exactly where you need it, when you need it and transformed exactly how you need it.

## Data Pipeline Overview
Data pipelines comprise the following sequential actions which require coordination, execution and monitoring:

1. [Inbound Data Automation](https://beepbeeptechnology.github.io/inbound/)
1. [Data Transformation](https://beepbeeptechnology.github.io/transformation/)
1. [Outbound Data Automation](https://beepbeeptechnology.github.io/outbound/)

## Google BigQuery

The most fundamental, foundational component of each data pipeline is your Data Warehouse.  

We exclusively use Google BigQuery due to its scaleability, ease of setup and use, powerful functionality set and pace of new feature release.  If you have a Google Cloud Platform account (set one up [here](https://cloud.google.com/gcp/) if not), then BigQuery is already available at [console.cloud.google.com/bigquery](https://console.cloud.google.com/bigquery).

 It is good to think of BigQuery as an external brain (built by some of the smartest people in the world), which can manage all of your data complexity, which scales to infinity and in most use cases is completely free of charge.  It is completely serverless, which means that you never have to think about turning it on/off, managing underlying infrastructure or anything except using it.
 
 It is, in a word, amazing.

Using BigQuery as the foundation, we then design, build, connect, deploy and manage your data pipeline components. 



