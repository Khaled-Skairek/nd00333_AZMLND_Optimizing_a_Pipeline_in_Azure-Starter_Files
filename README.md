# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**This dataset contains data about clients of a bank and we seek to predict if a client is going to apply for a loan"**

It is not possible to tell which model was the best by comparing best auto ml model to the logistic regressor since they both resulted into very similar prediction accuracy, namely: 0.91

## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
1- Read data stored in csv file
2- Clean data by removing irrelevant features
3- One hot encode
4- Split data into train/test sets
5- prepare training script to call logistic regression algorithm
6- Config hyper drive in Azure machine learning to call the training script several times with different hyper parameters
7- Run the hyper drive
8- Register the best model and save the found parameters 


**What are the benefits of the parameter sampler you chose?**
The hyper parameter "C" was sampled using an uniform distribution to increase the probability of choosing the optimal value.
The hyper parameter "max iteration" was sampled using choice function to reduce the number of tested parameters (which increases the speed of training)

**What are the benefits of the early stopping policy you chose?**
The early stopping policy helps to save time (money as well), the policy I chose helps to stop when no improvement was observed for two consecuitive runs.
## AutoML
The best model was "VotingEnsemble". It was aleady mentioned in previous lessons that most of the times, the best model generated by auto ml, would be ensemble model. Several models are trained. Each model votes for a prediction, the ensemble then choose the most likely class.

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
In terms of performance, the two best models were, as mentioned in the introduction, identical. I expected to find a difference before starting the project since Auto ML has the power of trying many algorithms and models. But due to time constraints and maybe the validity of the linear assumption, the logistic regressor lived up to the Auto ML best model.

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
- Try more parameters combination for the logistic regressor
- Give more time for the auto ML to try different models and hyper parameters
- Try different metrics for the auto ML
