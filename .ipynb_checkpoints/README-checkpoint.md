[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/7lKBcjfN)
# 44-566 machine-learning project
Repo for all project documents  

#### Early project update, change in dataset:
The original data or idea for the project was to use a US dataset, that contained data on health, to see if there is any relation between different diseases and being overweight. Due to the complexity of the dataset, a lack of interest in the dataset, and a lack of numerical values in the dataset that I could use for analysis I've decided to move to a Movie metadata dataset sourced or shared to me from Kaggle.
This new dataset can be found here: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset/data?select=movies_metadata.csv  
The specific file choses from the zip is movies_metadata.csv  

## Milestone 1 overview
#### Initial Exploration
Data importing started off with an error. Some of the data is fields that should have been numerical contained text that prevented the data from being imported into the correct type, this issue was fixed mainly by using "dropna". After fixing this issue I reduced the columns in the working set of data for milestone 1 into the four numerical features: budget, revenue, vote_average, and runtime.  
  
The initial_exploration of the dataset provided insights of the data from the info and value_count functions and scatter plots. The provided info allowed me to clean and filter data that either didn't exist or was set to a default value such as zero, although this did reduce my dataset from around 50k to around 10k. The scatter plot matrix allowed me to see relations between each column of data. From these plots I could see there is roughly a linear relation between budget and revenue, and somewhat normal relations between either budget or revenue to vote_average. Looking at the correlation between budget and revenue I could see it was high and decided to perform linear regression based on this.  
  
#### Linear Regression
Within the linear regression notebook I was able to create a model with an approximate accuracy of 55% using any of the following methods with little variation: ElasticNet, Elasticnet with multiple features, quadratic, and cubic. The quadratic set performed better than all other models by ~1%.  
While testing the models I made the change to not include both budgets that were set to a default of zero, and to budgets that were below 10K. The reason I did this is because out of the approximate 50k rows of data I had, for the purpose of calculating revenue from budget, I found that 40k of them were set to zero. After filtering the data. The percentage of the ElasticNet model droped from around 61% down to 54.4%.