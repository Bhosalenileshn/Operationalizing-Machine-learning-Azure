# Operationalizing-Machine-learning-Azure

This is the second Project for *Machine Learning with Microsoft Azure*. In this project we explore the below concepts.
 * Uploading Daaset to azure.
 * Creating a ML Model using AutoML from Azure ML studio as well as Pipeline from the Jupyter Notebook.
 * Deploying the model as HTTP REST API.
 * Creating a Swagger documentaion of Deployed HTTP REST API.
 * Using Apache Benchmark for Deployed Model.
 * Enabling the Applicaion Insights.
 * Consuming the Endpoint using JSON test file.
   
## Architectural Diagram  
![Architectural Diagram](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/ArchitectureDiagram2.png)  

As seen from the above Image we take the Following steps.

**Step 1** :  Creating a Compute cluster for the ML tasks we are going t perform  
![Compute Cluster](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/compute_cluster.png)  

**Step 2** : Registering the Bank Dataaset.  
  `This Dataset is regarding Bank-Marketing campain, which contains columns regarding age,marital status, contact type, type of job etc. We will use this dataset to    predict if the customer will subscribe to the term deposite.`   
  ![Registered Dataset](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/registerd_dataset.png)  

**Step 3**:  
### Using Azure AutoML Studio  
* We create the AutoML Experiment from Azure AutoML Studio. We use the Classification for our Task.
  AutoML took arount 22 mins to complete the training and finding the best Model.  
  ![AutoML Complete](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/autoMLrun%20complete.png)  
 
 
* Voting Ensemble was the best model AutoML selected with **Accuracy 0.92018** .  
  ![Best Model](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/autoML%20Best%20Model.png)  
  
* We Deployed the best model (Voting Ensemble) and we did not enabled the application insights at this stage.  
  ![Model Deploy](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/autoMLDeloyModel.png)  
  
* We Enabled the **Application Insights** for deployed model using [logs.py](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/logs.py)  
  ![App Insight](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/appInsightenabled.png)  
  
  `Below is the Screenshot of Enabled link.  `
    
  ![App Insight 2](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/applicationInsightlink.png)  
    
  `Below is the Screesnsot of running logs of logs.py  `  
  
  ![Logs.py](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/enablingApplicationInsight_logsscrpt.png)    
  
 * Swagger is used to create the documentaion for HTTP REST API endpoint of deployed model. [swagger.sh](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/swagger/swagger.sh) is used to run a swagger docker image and [serve.py](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/swagger/serve.py) is used to serve the `swagger.json` for our model on an HTTP server.    
 ![Swagger 1](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/swaggerURI_running.png)    
 ![Swagger 2](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/swaggerURI_running_2.png)    
 
 * We use [endpoint.py](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/endpoint.py) to consume the model. We provide the data to the model in the form of `JSON` using HTTP `POST` request. It Intracts with the Model and returns the result in form of `JSON` data.  
 ![endpoint.py](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/EndpointRun.png)    
   
 * Apache Benchmark is used to set the Benschmark for the deployed Model. We used [benchmark.sh](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/benchmark.sh) for this. It gives the parameters such as `time per request, number of request failed, request per second` etc.  
 ![Benchmark](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/benchmartRun_2.png)    
 ![benchmark2](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/benchmartRun_1.png)    
 

## Using Jupyter Notebook
[Jupyter Notebook](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/starter_files/aml-pipelines-with-automated-machine-learning-step.ipynb)    
We create the pipeline for the entire process in jupyter notebook.    

* Pipeline used AutoML to train the model. Below is the screenshot showing the submitted run through notebook.     
  
  ![pipeline automl running](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/JN_Pipeline_Run_endpoint%20running.png)    
  
  `Pipeline run is completed`    
  
  ![Pieline Run](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/JN_autoMLrun.png)   
  
 * Publishing the Pipeline through the Notebook. In below screenshot you can see the pipeline status is active i.e. pipline is published successfully.  
  ![pipline stutus](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/JN_Pipeline_published_1.png)    
  
  `In below image we can see that REST API is created for the published pipeline.`  
  
  ![published](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/JN_Pipeline_published_2.png)    
  
 * RunWidget Details.    
   ![Runwidget](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/JN_Pipeline_Runwidget.png)    
   

### Deleting the Compute Cluster    
![Delete Cmpute](https://github.com/Bhosalenileshn/Operationalizing-Machine-learning-Azure/blob/main/screenshots/delete_compute_cluster.png)    

## Screencast YouTube Link
[Screencast Link](https://youtu.be/PBOQOW3wr7k)  

## Future Work    
* We can use different selected algorithms and try to find the best parameters using HyperDrive.  
* We can try and use Deep Learning to check if it increases the Performance.  
* We can consult to the person with the domain knowledge to decide which colums are irrelevant and which are relevant. We can also gather data from different       banks and check whether the data is same and if different hot it is affecting the outcome.   

  
  

  
  
