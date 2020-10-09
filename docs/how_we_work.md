# How we work
We have a fully remote team based in the European Union, but with some flexibility to ensure that we can find overlap in terms of working hours with global clients.  

Our registered office is in Dublin, Ireland and we can invoice in EUR, USD, GBP or AUD.

## Initial Interest
If you are interested in potentially using any of our services, please contact us at [info@beepbeep.technology](mailto:info@beepbeep.technology) and we will get back to you within 48hrs to set up an initial consultation.  This gives us the time to investigate any non-standard requirements in advance of an initial scoping call.


## Project Scoping
We will then schedule an initial scoping video call to clarify any additional information and work through specific options available, as well as the likely trade-offs between up-front effort and ongoing management.  We will also discuss options regarding infrastructure deployment and management, as well as any training requirements.
  
  Following this call we will be able to provide a high-level design outline and an indicative proposal.  There will be more certainty over effort required for core services and we will highlight any areas where estimation uncertainty is higher.

## Operating Model
You will also need to decide on the type of operating model under which you want to engage our services.  This should be tailored to your individual needs, as well as the level of resources you want to apply to managing your data pipelines in future, and the capabilities of your internal resources.

The type of model selected will impact the up-front and ongoing costs.
    
=== "Fully Managed"
    In this approach we set all of your resources up on our managed infrastructure, and we take responsibility for ongoing resource management, quality assurance and ultimately data delivery.  Your GCP project will only need to contain the BigQuery dataset and any other scoped Google destinations.
        
    As we develop and upgrade our resources, you will also have access to new functionality and tools.  We will also take full responsibility for ongoing troubleshooting and pipeline fixes as and when they arise to ensure your data pipelines continue to function reliably.
        
    | Cost | Level | Description |
    | -- | -- | -- |
    | Initial Cost | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:| Lower initial setup cost as we leverage existing operating infrastructure |
    | Ongoing Cost | :material-circle: :material-circle: :material-circle-outline: :material-circle-outline:| Higher ongoing cost as we manage and monitor resources and data pipelines |
      
=== "Hybrid Model"
    In this more flexible model, we can agree on which resources and processes you want to be managed by us, and what you want to manage in-house.  The more resources we need to deploy on your GCP infrastructure for in-house management, the higher up-front cost but lower ongoing cost.
  
      You will also have access to new functionality and tools for any resource which remain on our infrastructure.  We can also take responsibility for ongoing troubleshooting and pipeline fixes as and when they arise to ensure your data pipelines continue to function reliably.  
    

    | Cost | Level | Description |
    | -- | -- | -- |
    | Initial Cost | :material-circle: :material-circle: :material-circle: :material-circle-outline:| Medium initial cost as we leverage some existing operating infrastructure |
    | Ongoing Cost | :material-circle: :material-circle-outline: :material-circle-outline: :material-circle-outline:| Ongoing cost dependant on scope of monitoring/management services |
    
=== "Self Managed"
    In this approach we will clone our source code and deploy replicas of our resources onto your Google Cloud Platform project, and you will have full ownership rights over all components.   We will provide you with tools and guidelines to monitor your data pipelines and you will have full responsibility for management, ongoing troubleshooting and pipeline fixes.  If you require any additional services, this will be treated as a new engagement.
    
    You will not have access to new functionality and tools as we develop and upgrade our resources.

    | Cost | Level | Description |
    | -- | -- | -- |
    | Initial Cost | :material-circle: :material-circle: :material-circle: :material-circle:| Higher initial cost as we sign over a snapshot of our code base|
    | Ongoing Cost | :material-circle-outline: :material-circle-outline: :material-circle-outline: :material-circle-outline:| No ongoing cost as you have full responsibility for monitoring/management |

## Project Phases
Project structure will be tailored to your specific needs, however it will typically involve some or all of the following phases.

=== "Design"
    Following on from your initial brief and our subsequent scoping, we will draw up a high-level end-to-end design, comprising all of the data sources, destinations, components, refresh requirements and other specifications unique to your requirements.  This will also include information on resource management responsibility
    
=== "Setup"
    At this stage we set up the Google Cloud Platform project, set up access controls and generate the credentials we need to interact with project resources.  The setup here will vary depending on the comfort level you have with managing Google Cloud resources, and the model you want to operate in the future.
    
=== "Test"
=== "Deploy"
=== "Document"
=== "Train"
=== "Monitor"
=== "Maintain"


