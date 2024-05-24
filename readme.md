<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="60px" src="https://hermes.dio.me/lab_projects/badges/87d332d0-5198-4a2f-b159-38c8c2976954.png"></a>
    <span> Trabalhando com Machine Learning</span>
</h1>

Explore Automated Machine Learning in Azure Machine Learning
In this exercise, you’ll use the automated machine learning feature in Azure Machine Learning to train and evaluate a machine learning model. You’ll then deploy and test the trained model.



# Create an Azure Machine Learning workspace
To use Azure Machine Learning, you need to provision an Azure Machine Learning workspace in your Azure subscription. Then you’ll be able to use Azure Machine Learning studio to work with the resources in your workspace.

Tip: If you already have an Azure Machine Learning workspace, you can use that and skip to the next task.

Sign into the Azure portal at https://portal.azure.com using your Microsoft credentials.

# Step-by-Step Guide to Creating and Deploying an Azure Machine Learning Resource

## Create an Azure Machine Learning Resource

1. **Select + Create a resource**
2. **Search for "Machine Learning"**
3. **Create a new Azure Machine Learning resource** with the following settings:
    - **Subscription**: Your Azure subscription.
    - **Resource group**: Create or select a resource group.
    - **Name**: Enter a unique name for your workspace.
    - **Region**: Select the closest geographical region.
    - **Storage account**: Note the default new storage account that will be created for your workspace.
    - **Key vault**: Note the default new key vault that will be created for your workspace.
    - **Application insights**: Note the default new application insights resource that will be created for your workspace.
    - **Container registry**: None (one will be created automatically the first time you deploy a model to a container).
4. **Select Review + create**, then **select Create**.
5. **Wait for your workspace to be created** (it can take a few minutes), and then go to the deployed resource.
6. **Select Launch studio** (or open a new browser tab and navigate to [Azure Machine Learning Studio](https://ml.azure.com), and sign into Azure Machine Learning studio using your Microsoft account).
7. **Close any messages that are displayed**.
8. **In Azure Machine Learning studio**, you should see your newly created workspace. If not, select **All workspaces** in the left-hand menu and then select the workspace you just created.

## Use Automated Machine Learning to Train a Model

Automated machine learning enables you to try multiple algorithms and parameters to train multiple models, and identify the best one for your data. In this exercise, you’ll use a dataset of historical bicycle rental details to train a model that predicts the number of bicycle rentals that should be expected on a given day, based on seasonal and meteorological features.

1. In Azure Machine Learning studio, view the **Automated ML page** (under Authoring).
2. **Create a new Automated ML job** with the following settings, using **Next** as required to progress through the user interface:

### Basic Settings
- **Job name**: mslearn-bike-automl
- **New experiment name**: mslearn-bike-rental
- **Description**: Automated machine learning for bike rental prediction
- **Tags**: none

### Task Type & Data
- **Select task type**: Regression
- **Select dataset**: Create a new dataset with the following settings:

#### Data Type
- **Name**: bike-rentals
- **Description**: Historic bike rental data
- **Type**: Tabular

#### Data Source
- **Select From web files**
- **Web URL**: https://aka.ms/bike-rentals
- **Skip data validation**: do not select

#### Settings
- **File format**: Delimited
- **Delimiter**: Comma
- **Encoding**: UTF-8
- **Column headers**: Only first file has headers
- **Skip rows**: None
- **Dataset contains multi-line data**: do not select

#### Schema
- **Include all columns other than Path**
- **Review the automatically detected types**
- **Select Create**. After the dataset is created, select the bike-rentals dataset to continue to submit the Automated ML job.

### Task Settings
- **Task type**: Regression
- **Dataset**: bike-rentals
- **Target column**: Rentals (integer)

#### Additional Configuration Settings
- **Primary metric**: Normalized root mean squared error
- **Explain best model**: Unselected
- **Use all supported models**: Unselected (you’ll restrict the job to try only a few specific algorithms).
- **Allowed models**: Select only RandomForest and LightGBM

#### Limits
- **Max trials**: 3
- **Max concurrent trials**: 3
- **Max nodes**: 3
- **Metric score threshold**: 0.085
- **Timeout**: 15
- **Iteration timeout**: 15
- **Enable early termination**: Selected

#### Validation and Test
- **Validation type**: Train-validation split
- **Percentage of validation data**: 10
- **Test dataset**: None

### Compute
- **Select compute type**: Serverless
- **Virtual machine type**: CPU
- **Virtual machine tier**: Dedicated
- **Virtual machine size**: Standard_DS3_V2* (If your subscription restricts the VM sizes available to you, choose any available size.)
- **Number of instances**: 1

3. **Submit the training job**. It starts automatically.
4. **Wait for the job to finish**. It might take a while — now might be a good time for a coffee break!

## Review the Best Model

When the automated machine learning job has completed, you can review the best model it trained.

1. **On the Overview tab** of the automated machine learning job, note the best model summary.
![complete-run](https://github.com/jefteralex1/Microsoft-Azure-AI-Fundamentals/assets/103465537/5c35f738-dd23-4a84-9032-f8ce4feba560)
3. **Select the text under Algorithm name** for the best model to view its details.
4. **Select the Metrics tab** and select the residuals and predicted_true charts if they are not already selected.
5. **Review the charts** which show the performance of the model.

## Deploy and Test the Model

1. On the **Model tab** for the best model trained by your automated machine learning job, select **Deploy** and use the Web service option to deploy the model with the following settings:
    - **Name**: predict-rentals
    - **Description**: Predict cycle rentals
    - **Compute type**: Azure Container Instance
    - **Enable authentication**: Selected
2. **Wait for the deployment to start** - this may take a few seconds. The Deploy status for the predict-rentals endpoint will be indicated in the main part of the page as Running.
3. **Wait for the Deploy status to change to Succeeded**. This may take 5-10 minutes.

### Test the Deployed Service

1. In Azure Machine Learning studio, on the left hand menu, select **Endpoints** and open the **predict-rentals real-time endpoint**.
2. On the **predict-rentals real-time endpoint page**, view the **Test tab**.
3. In the **Input data to test endpoint pane**, replace the template JSON with the following input data:

```json
{
  "Inputs": { 
    "data": [
      {
        "day": 1,
        "mnth": 1,   
        "year": 2022,
        "season": 2,
        "holiday": 0,
        "weekday": 1,
        "workingday": 1,
        "weathersit": 2, 
        "temp": 0.3, 
        "atemp": 0.3,
        "hum": 0.3,
        "windspeed": 0.3 
      }
    ]    
  },   
  "GlobalParameters": 1.0
}
```

4. **Click the Test button**.
5. **Review the test results**, which include a predicted number of rentals based on the input features - similar to this:

```json
{
  "Results": [
    444.27799000000000
  ]
}
```

The test pane took the input data and used the model you trained to return the predicted number of rentals.

## Clean-Up

1. In Azure Machine Learning studio, on the **Endpoints tab**, select the **predict-rentals endpoint**.
2. Select **Delete** and confirm that you want to delete the endpoint.

### To Delete Your Workspace

1. In the Azure portal, in the **Resource groups** page, open the resource group you specified when creating your Azure Machine Learning workspace.
2. Click **Delete resource group**, type the resource group name to confirm you want to delete it, and select **Delete**.
