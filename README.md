[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/7lKBcjfN)
# 44-566 machine-learning project
Repo for all project documents  

#### Links to other documents
2. [Raw data](RAW_DATA.md)
3. [Data](DATA.md)
4. [Analysis](ANALYSIS.md)
5. [Conclusions](CONCLUSIONS.md)

## Introduction and goals
This project aims to predict the genre of a movie from its metadata features. This list of features includes: budget, revenue, vote average, and vote count after a reduction. In order to find out if it's possible, this project will test the dataset against different models inlcuding linear regression, classification, and decision trees. It will also test these models with different feature combinations.

#### Early project update, change in dataset:
The original data or idea for the project was to use a US dataset, that contained data on health, to see if there is any relation between different diseases and being overweight. Due to the complexity of the dataset, a lack of interest in the dataset, and a lack of numerical values in the dataset that I could use for analysis I've decided to move to a Movie metadata dataset sourced or shared to me from Kaggle.
This new dataset can be found here: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset/data?select=movies_metadata.csv  
The specific file chosen from the zip is movies_metadata.csv  

## Milestone 1 overview
#### Initial Exploration
Data importing started off with an error. Some of the data is fields that should have been numerical contained text that prevented the data from being imported into the correct type, this issue was fixed mainly by using "dropna". After fixing this issue I reduced the columns in the working set of data for milestone 1 into the four numerical features: budget, revenue, vote_average, and runtime.  
  
The initial_exploration of the dataset provided insights of the data from the info and value_count functions and scatter plots. The provided info allowed me to clean and filter data that either didn't exist or was set to a default value such as zero, although this did reduce my dataset from around 50k to around 10k. The scatter plot matrix allowed me to see relations between each column of data. From these plots I could see there is roughly a linear relation between budget and revenue, and somewhat normal relations between either budget or revenue to vote_average. Looking at the correlation between budget and revenue I could see it was high and decided to perform linear regression based on this.  

#### Linear Regression
Within the linear regression notebook I was able to create a model with an approximate accuracy of 55% using any of the following methods with little variation: ElasticNet, Elasticnet with multiple features, quadratic, and cubic. The quadratic set performed better than all other models by ~1%.  
While testing the models I made the change to not include both budgets that were set to a default of zero, and to budgets that were below 10K. The reason I did this is because out of the approximate 50k rows of data I had, for the purpose of calculating revenue from budget, I found that 40k of them were set to zero. After filtering the data. The percentage of the ElasticNet model droped from around 61% down to 54.4%.

## Milestone 2 overview
#### Classification
Within the classification notebook I performed an analysis on the predictive power of a movies revenue and vote_average to be able able to predict a movies genre.  

The process started with cleaning data. The genres feature contained a list of objects that contained all of the genres for a specific movie. In order to transform this column into something I could use I ended up "exploding" the data. A single row with multiple genres was transformed into multiple rows containing the same data with the only difference being that the genres column would contain a single genre. After cleaning and transforming the data there were shown to be 18k rows. 

The two models I used were decision tree and svc rbf. Starting with the decision tree. An analysis over the train set showed a poor predictive power to predict genre. The accuracy of the model on the train was 46% and the F1 score was .41. These results are low but much higher than expected. They suggest that there's nearly a 50% chance to guess the genre based on the previous features. It becomes more interesting when looking at the test set. The test set showed a much higher accuracy and F1-score, both at .81. I do not currently know why the training and test set show such a massive difference.  

The scv rbf model used had an accuracy of 20% and an F1-score of .09. These numbers were consistant between the training set and the test set.  

## Milestone 3 overview
#### KMean clusters and Dimension
Here I've started updating the data cleaning section to include transforming the individual genres into numbers. The overall effect of results does not appear to be significant. I've noticed changes of 1-2% accross models.  
The KMean cluster analysis and the Dimension analysis both performed poorly with the given data. It is hard to tell if there is anything wrong with the data. The only thing I can think of that may cause issues is splitting based on included genres, but even then the data appears to only double in size, from around 5k to 11k. The KMean clustering on the dataset did not for uniform groups for any of the 20 genres in the set. KMeans was tested with cluster sizes of 20 and 10 with either giving poor results.  
The PCA tool did not perform any better than KMeans. I did not have many cleaned features I was working with to begin with. Of the 4-5 I tested the resulting variance on them resulted in most of them having a cumsum of 1. I found that if there isn't a lot of variation in values this can happen. After testing whether this may be caused from duplicate values after duplicating items by splitting genres, I concluded that the duplication is likely less of a problem than it seems. The 4-5 features I'm testing may each simply have a high impact on prediction. I ended up without a curve on the PCA graph, instead there was a straight line that didn't have much impact on the SVC model I tested the few values I could against.

#### Anomalous data
While testing the data I noticed that the ensemble performed poorly on the training set and about as good as it could get on the training set. The training set deals with a smaller amount of data, but it should still be around 2.5k entries. I reviewed the SVC model inside the ensemble that showed similar performance in a run I performed under the ensemble run, and I checked the performance of this SVC in a previous notebook from that hint. There I could see that although the model has a poor accuracy and f1 score, about 20% and 10% respectively. It's overall performance greatly depends on only a few of the genres it tries to find. This is despite the genres being mostly spread out with each containing hundreds. It appears that only some of the data in my data set is able to be predicted linearly somewhat, and this data messed with my ensemble predictions when working with a smaller dataset. Or at least that is what it appears.

## Conclusion
From the data set that I've pulling this conclusion from, it looks like a genre can be predicted with an accuracy of 45%. The data itself appears to best fit in a decision tree style classifier. There were no patters identifiable within the KMeans classifier. Checking the PCA curve did not result in an elbow I could reduce the data from with a better result. The linear regression methods did not perform well either.