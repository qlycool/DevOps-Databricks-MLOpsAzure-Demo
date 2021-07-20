# Introduction 

This project demonstrates the use of Azure DevOps as the tool to work with ML Pipelines in Azure Databricks.-

Workflow Steps

- Data Scientist promotes model into Staging (e.g. as in the kedro_mlflow_training Notebook)
- Pipeline gets triggered (via Webhooks, manually or via API, as in the kedro_mlflow_training Notebook)
- Azure Dev Ops uploads deployment notebook (deploy_azure_ml_model) from git to a dedicated Test/QA region within the workspace via the Databricks workspace API
- Azure Dev Ops runs deploy notebook with creater job and run submit which does the following:
    - Retrieves latest model staging from registry
    - Deploys model as an Azure ML model and creates an image
    - Deploys REST API for he model/image
    - returns an the REST API deployment URL to Azure Dev Ops
- Azure Dev Ops uploads test notebook from git to a dedicated Test/QA region within the workspace
- Azure Dev Ops runs deploy notebook with run submit which does the following:
    - Retrieves test data
    - Invokes REST API
- If successful, DevOps will deploy the model into production using the mlFlow REST API# databricksMLOpsAzureDemo

# Tested successfull on DevOps

# References:
https://github.com/koernigo/databricksMLOpsAzureDemo
![image](https://user-images.githubusercontent.com/35471410/126400795-ec9508df-a06c-49c8-80c7-92f0fa8af612.png)

https://www.youtube.com/watch?v=4olCJWwZsVQ
![image](https://user-images.githubusercontent.com/35471410/126400819-757d1d57-251d-4445-bcf7-d9a664647c31.png)
