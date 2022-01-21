# NBA-Shot-Predictor
Predicting NBA Shot Outcome using play-by-play data
This document discusses the problem, hypothesis, methodology, conclusion, and tools used to undertake the project.
Technologies and Tools used:

Python,Pandas,NumPy,MatPlotlib, Seaborn, Scikit-learn(Machine Learning), Jupyter Notebook

# Problem:
          
The 2015-16 season was one of the most exciting NBA seasons in modern times. Shooting is an important part of basketball and I thought it would be interesting to see the most important factors in the success of the shot. 
The main target audience of this project would be:
* NBA teams (players and staff)
* Sports analysts 
* Sports betting companies(possibly)

The main target is the Shot Outcome, make or miss. The purpose is to create a model that predicts at a relatively(to the baseline) high accuracy.

NBA plays and shots
Plays: NBA plays are carried out by the offensive team(team who has the ball). It can end in many ways, not necessarily a shot. Stolen, out of bounds,fouled,ball fumbled, time up etc.

Two types of endings to a play - Shot or No Shot
We are only interested in the plays. 

# Data Acquisition:

The data acquisition was fairly simple. The data was taken from basketball-reference.com. It is a play-by-play dataset of all the plays in the 2015-16 season. 
Hence, the acquisition was simply downloading the data as a .csv file.

# Data Cleaning and Exploratory Data Analysis(EDA):

All the work in this project was done in a Jupyter notebook using Python and its packages. 


The data overall was quite clean. However this did not mean there weren't any unnecessary columns. The data consisted of approximately 600,000 rows and 40 columns. 

Summary of steps: 
* Remove plays that do not end in a shot 
* Shot Outcome with null values were dropped 
* Columns that are unnecessary towards the outcome such as URL,location etc were removed. 

Exploratory Data Analysis involves exploring the data and selecting the variables for further modeling. It was interesting to see the variables as numerical and categorical.     
The shot Outcome is the target variable: 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image11.png)

For the Numerical Variables: 


There are 5 numerical variables : Quarter, SecLeft, AwayScore, HomeScore, ShotDist

Quarter, SecLeft and ShotDist seem the most relevant for predictions. Scores don't seem so.

Here are the basic plots for numerical variables to measure frequency/count number of values: 


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image13.png)















Kernel Distribution plots are useful for understanding the relationship between variables. 
Here I made a few alongside regular frequecy plots- 

Shot Distance vs Outcome (KDE):

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image14.png)


Frequency of Shot Distance in feet(ft.): 


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image1.png)


SecondLeft vs Outcome (KDE): 


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image5.png)



Frequency of Seconds Left: 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image7.png)


Quarter vs Outcome (KDE):

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image16.png)




Shot Distance appears to be the biggest influencer.
Seconds Left and Quarter are smaller but not insignificant. 
Home and Away Scores seem quite insignificant. Can be ignored. 


Categorical Variables:


There are 31 categorical variables. Most were removed during the cleaning process. Many are not shot related. Most seem inconsequential to the target. Only 3 seemed interesting, the rest were rejected. 
Relevant ones: ShotType, ShotOutcome, Shooter, Assister 



ShotType:
![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image17.png)

Shooters:

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image10.png)

Assisters:

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image4.png)




Final Variable Selection:
From the EDA we can finally confirm the variables for modeling. 

Target: 
* Shot Outcome

Variables:

* Shot Distance 
* Seconds Left in the quarter 
* Quarter
* Shot Type
* Assister 
* Shooter




# Modeling and Predictions:  

I ran 3 main models :
* Logistic Regression 
* Random Forests 
* Decision Trees

Logistic Regression:

We get an accuracy of 81.52%. This is a strong score relative to the baseline of 54%.
Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image12.png)




Decision Trees: 

For the decision tree we get a weaker score but still better than the baseline accuracy. It has an accuracy score of 62%. 

Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image3.png)


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image6.png)


Random Forests:

Similar to the decision tree the random forests also give us a score weaker than the logistic regression. 
Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image15.png)
![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image2.png)




However, the random forests help us calculate the feature importance to see which features were the most impactful for predicting the shot outcome. 






# Feature importance:
This is great in understanding the importance factors for shot outcome. It's clear that shot distance and shot type are major factors followed by the assisters and the seconds left. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image9.png)



# Conclusion:

* The Logistic Regression model performs the best at predicting the Outcome with an accuracy score of 81%. A strong improvement over the baseline(54%). 
* The other two models, Random forests and Decision Trees are not as good but still better than baseline at approximately 61/62%.
* Other models like SVM,XGBoost were tried but not so great. 
* All the models show no signs of overfitting/underfitting. They are accurate. 
* Shot Distance and Shot Type are the major factors influencing shot outcomes. Followed by Assisters.  




# Key Takeaways and Moving Forward: 

* I could have used a shot log dataset over a play by play-by-play dataset. There could be more variables that may help in predicting target(ShotOutcome) better.
Adding more seasons and increasing the size of the dataset. This would be more representative of the players. 
* Working on improving scores in Random Forests/Decision Trees. These scores were underwhelming compared to Logistic Regression. 
* Applying other models as well, Neural Nets, k-NN.
* Spend less time doing EDA, more time modeling. 
* Creating a recommendation system based on players. Recommend shots type + distance.
* Use a shot log dataset that could help create a more accurate model. 

