# Build a Movie Recommendation System with Azure Machine Learning service
Recommendation systems are used in a variety of industries, from retail to news and media. If you’ve ever used a streaming service or ecommerce site that has surfaced recommendations for you based on what you’ve previously watched or purchased, you’ve interacted with a recommendation system. With the availability of large amounts of data, many businesses are turning to recommendation systems as a critical revenue driver. However, finding the right recommender algorithms can be very time consuming for data scientists. This is why Microsoft has provided a [GitHub repository](https://github.com/Microsoft/Recommenders) with Python best practice examples to facilitate the building and evaluation of recommendation systems. You can learn more about the repo on the [Azure Blog](https://azure.microsoft.com/en-us/blog/building-recommender-systems-with-azure-machine-learning-service/).

This tutorial will walk through how to build a Movie Recommender system trained with a Simple Algorithm for Recommenders (SAR) for the [Movielens dataset](https://grouplens.org/datasets/movielens/) on [Azure Machine Learning service](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml). It demonstrates how to use the power of the cloud to manage data, switch to powerful GPU machines, and monitor runs while training a model. You will also be able to test an existing webservice and find the most relevant movie recommendations.

In this lab you will:

- Connect to an Azure Machine Learning service workspace
- Access Movielens data from a datastore
- Connect to CPU and GPU machines from [Azure Machine Learning Compute](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-set-up-training-targets#amlcompute)
- Create a training script using the recommender repo's [util functions](https://github.com/Microsoft/Recommenders/tree/master/reco_utils) for SAR and add logging information
- Submit the training job to AzureML, and monitor the run with a jupyter widget
- Test an existing model with new user data
- **Optional part 2:** Deploy the model to a web service using Azure Container Instance. 

## Getting Started

1. Clone this repository in Azure Notebooks[![Azure Notebooks](https://notebooks.azure.com/launch.svg)](https://notebooks.azure.com/heatherbshapiro/projects/pycon-recommender?clone=true) 
2. Open the `sar_movielens_with_azureml.ipynb` notebook and run through the lab.
3. **Optional**: Run through the `deploy_with_azureml.ipynb` jupyter notebook

## What is Azure Machine Learning service?
The **[Azure Machine Learning service (AzureML)](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)** provides a cloud-based environment you can use to prep data, train, test, deploy, manage, and track machine learning models. By using Azure Machine Learning service, you can start training on your local machine and then scale out to the cloud. With many available compute targets, like [Azure Machine Learning Compute](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-set-up-training-targets#amlcompute) and [Azure Databricks](https://docs.microsoft.com/en-us/azure/azure-databricks/what-is-azure-databricks), and with [advanced hyperparameter tuning services](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-tune-hyperparameters), you can build better models faster by using the power of the cloud.

Data scientists and AI developers use the main [Azure Machine Learning Python SDK](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/intro?view=azure-ml-py) to build and run machine learning workflows with the Azure Machine Learning service. You can interact with the service in any Python environment, including Jupyter Notebooks or your favorite Python IDE. The Azure Machine Learning SDK allows you the choice of using local or cloud compute resources, while managing and maintaining the complete data science workflow from the cloud.
![AzureML Workflow](https://docs.microsoft.com/en-us/azure/machine-learning/service/media/overview-what-is-azure-ml/aml.png)

### Advantages of using AzureML:
- Manage cloud resources for monitoring, logging, and organizing your machine learning experiments.
- Train models either locally or by using cloud resources, including GPU-accelerated model training.
- Easy to scale out when dataset grows - by just creating and pointing to new compute target

