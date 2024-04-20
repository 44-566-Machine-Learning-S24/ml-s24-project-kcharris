[readme](README.md)  

#### Linear Regression  
Three models were used: ElasticNet, Quadratic, and Cubic. Elastic net was used twice. The original data and the summary go over these linear models ability to predict a revenue from different feartures.
Elastic net with x = budget had a score of .54
Elastic net with x = budget, vote_average had a score of .556
Quadratic LinearRegression with x = budget had a score of .567
Cubic LinearRegression with x = budget had a score of .557

Based on these scores budget has about a 50% relation with the revenue of a movie.

I did not have the Genres split into something that a Linear regression model could handle at the time. I went through and ran it after a copy paste of my data cleaning cell from a later stage in the process. The results show a consistent .007 for the R^2 score. The linear regression model does not perform well for my data at all.

#### Classification

#### Clustering and Dimensional Analysis

#### Ensemble

#### Additional