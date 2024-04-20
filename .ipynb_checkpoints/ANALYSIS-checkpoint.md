[Back to readme](README.md)  

#### Linear Regression  
[Linear Notebook](linear_regression.ipynb)  
Three models were used: ElasticNet, Quadratic, and Cubic. Elastic net was used twice. The original data and the summary go over these linear models ability to predict a revenue from different feartures.

Elastic net with x = budget had a score of .54
Elastic net with x = budget, vote_average had a score of .556
Quadratic LinearRegression with x = budget had a score of .567
Cubic LinearRegression with x = budget had a score of .557

Based on these scores budget has about a 50% relation with the revenue of a movie.
![Linear_Reg](fig/linear_reg.png)

[Linear Final Notebook](linear_final.ipynb)  
I did not have the Genres split into something that a Linear regression model could handle at the time of the milestone. I went through and ran it after a copy paste of my data cleaning cell from a later stage in the process. The results show a consistent .007 for the R^2 score. The linear regression model does not perform well for my data at all.
![Linear_Reg](fig/linear_final.png)

#### Classification
[Classification](classification.ipynb)  
Classification models performed the best overall. The two models used were Decision Tree and SVC rbf.  

Decision Tree  
* F1 Score = 0.402
* Accuracy = 0.452

SVC rbf
* F1 Score = 0.088
* Accuracy = 0.196

The rbf model performed worse than the decision tree. My understanding is the rbf can check for linear and clustering relationships which are not represented by the decision trees structure.  

#### Clustering and Dimensional Analysis  
[Dimensional Analysis](DimensionalAnalysis.ipynb)  
This is the worste section for my data. Having more than one feature for most tests I tried a PCA analysis on my features only to be given this line. I did notice that my data shouldn't perform better with more than two features and ended up using just with without PCA modification for Kmeans.  
![PCA](fig/pca.png)  

The cluster analysis I performed was mainly visual, and based on the resulting graph I could see no clustering of use for the project. Clustering does not appear to perform well for the Data Set.  
![kmeans](fig/kmeans.png)

#### Ensemble
The last model that I tried was ensemble. Where I tried all of my my best performing models together. This includes a new RandomForest model.  

RandomForest  
* F1 Score = 0.451
* Accuracy = 0.452

All together  
* F1 Score = 0.261
* Accuracy = 0.336

All together the performance dropped considerably. Both SVC with linear quadradic kernel (in a pipeline) and SVC rbf both had low F1 Score around .1 that must have dropped the ensembles score. Funny enough. Performing the ensemble on test data in this notebook with the same setup for the first one resulted in a much higher score. I was left wondering if the individual f1 scores for each genre had an influence on the result, because the SVC models performed kind of well in one or two genres.  

#### Additional  
##### Improvement 
One thing that could be improved in my analysis is putting my data into a neural net. Based on the performace accross all models I think the accuracy of the models could be improved by 3 to 5 percent from the Random Forest example.  

##### Extra graphs
F1 score by model  
![Score by model](fig/F1ScoreByModel.png)  
Breakdown of SVC model  
![Quadratic breakdown](fig/QuadraticF1ScorePerGenre.png)