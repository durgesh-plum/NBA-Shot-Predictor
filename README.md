# NBA-Shot-Predictor
Predicting NBA Shot Outcome using play-by-play data
This document discusses the problem, hypothesis, methodology, conclusion, and tools used to undertake the project.
Technologies and Tools used:

Python,Pandas,NumPy,MatPlotlib, Seaborn, Scikit-learn(Machine Learning), Jupyter Notebook

Problem:

The 2015-16 season was one of the most exciting NBA seasons in modern times. Shooting is an important part of basketball and I thought it would be interesting to see the most important factors in the success of the shot. 
The main target audience of this project would be:
NBA teams (players and staff)
Sports analysts 
Sports betting companies(possibly)

The main target is the Shot Outcome, make or miss. The purpose is to create a model that predicts at a relatively(to the baseline) high accuracy.

NBA plays and shots
Plays: NBA plays are carried out by the offensive team(team who has the ball). It can end in many ways, not necessarily a shot. Stolen, out of bounds,fouled,ball fumbled, time up etc.
Two types of endings to a play - Shot or No Shot
We are interested only in plays. 

Data Acquisition 

The data acquisition was fairly simple. The data was taken from basketball-reference.com. It is a play-by-play dataset of all the plays in the 2015-16 season. 
Hence, the acquisition was simply downloading the data as a .csv file.

Data Cleaning and Exploration 
All the work in this project was done in a Jupyter notebook using Python and its packages. 


The data overall was quite clean. However this did not mean there weren't any  unnecessary columns. The data consisted of approximately 600,000 rows and 40 columns. 

Summary of steps: 
Remove plays that do not end in a shot 
Shot Outcome with null values were dropped 
Columns that are unnecessary towards the outcome such as URL,location etc were removed. 

Exploratory Data Analysis involves exploring the data and selecting the variables for further modeling. It was interesting to see the variables as numerical and categorical.     
The shot Outcome is the target variable: 



















For the Numerical Variables: 

There are 5 numerical variables : Quarter, SecLeft, AwayScore, HomeScore, ShotDist
Quarter, SecLeft, ShotDist seem the most relevant to the target. Scores not so much.


















Kernel Distribution plots are useful for understanding the relationship between variables. 
Here I made a few :



Frequency of Shot Distance in feet










Frequency of Seconds Left







Shot Distance appears to be the biggest influencer.
Seconds Left and Quarter are smaller but not insignificant. 
Home and Away Scores seem quite insignificant. Can be ignored. 


Categorical Variables 


There are 31 categorical variables. Many are not shot related. Most seem inconsequential to the target. Only 3 are interesting, rest can be rejected. 
Relevant ones: ShotType, ShotOutcome, Shooter, Assister 










ShotType












Shooters and Assisters






Shot Distance 
Seconds Left in the quarter 
Quarter
Shot Type
Assister 
Shooter




Modeling and Predictions  

I ran 3 models :
Logistic Regression 
Random Forests 
Decision Trees
Logistic Regression 
We get an accuracy of 81.52%. This is a strong score relative to the baseline of 54%.
This is the confusion matrix for logistic regression.





Decision Tree

For the decision tree we get a weaker score but still better than the baseline accuracy. 





Random Forests 

Similar to the decision tree the random forests also give us a score weaker than the logistic regression. 
Below is the confusion matrix and the various scores such as the precision, recall, and f-1 score. 










However, the random forests help us calculate the feature importance to see which features are the most impactful for calculating the shot outcome. 

















Feature importance 
This is great in understanding the importance factors for shot outcome. It's clear that shot distance and shot type are major factors followed by the shot assisters and seconds left. 




Conclusion 

The Logistic Regression model performs the best at predicting the Outcome with an accuracy score of 81%. A strong improvement over the baseline(54%). 
The other two models, Random forests and Decision Trees are not as good but still better than baseline at approximately 61/62%.
Other models like SVM,XGBoost were tried but not so great. 
All the models show no signs of overfitting/underfitting. 

Shot Distance and Shot Type are the major factors influencing shot outcomes.
Followed by Assisters.  















Key Takeaways and Moving Forward

I could have used a shot log dataset over a play by play-by-play dataset. There could be more variables that may help in predicting target(ShotOutcome) better.
Adding more seasons and increasing the size of the dataset. This would be more representative of the players. 
Working on improving scores in Random Forests/Decision Trees. These scores were underwhelming compared to Logistic Regression. 
Applying other models as well, Neural Nets, k-NN.
Spend less time doing EDA, more time modeling. 
Creating a recommendation system based on players. Recommend shots type + distance.
Use a shot log dataset that helps create a more accurate model. 

