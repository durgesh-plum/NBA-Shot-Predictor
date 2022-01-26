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

Exploratory Data Analysis involved exploring the data and selecting the variables for further modeling. The whole process helped underline all the trends and factors towards the target. The plots and graphs below highlight these relationships between them. 

The variables were divided into two: numerical and categorical. There were 5 numerical variables and 31 categorical variables. 

First step involved displaying and exploring basic information of the data. This involved but not limited to looking at the rows and columns, counting the number of values in each variable, number of types of each variable and so on. It was fairly straightforward figuring out which feature would be impactful or not. Plots showing insignificant relationships were rejected. The rest were selected. This was done mainly for the numerical variables. 

Summarizing the data using crosstab function also helps displaying the frequency with which certain data points appear with respect to the ShotOutcome function. The value counts functions also helped in this regard.
     
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


There are 31 categorical variables. The majority are not shot related. Most seem inconsequential to the target. Only 3 seemed interesting, the rest can be rejected. Almost all of them were removed after the cleaning process since they are inconsequential to shooting. 
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

* Shot Distance - The distance between the shooters position to the basketball hoop. This can range from 0 to 92 feet.
* Quarter - Basketball games have 4 quarters. Each 12 minutes long.
* Seconds Left in the quarter  - The number of seconds left in the quarter when the shot is taken.  
* Shot Type - There are quite a few types of shots as shown above. Jump shot, layup and dunk are among the most common. 
* Assister - The assister is the player who passes the ball to the shooter. A shooter has to make a successful shot for an assist to be counted.
* Shooter - The player who shoots the ball. 





# Modeling and Predictions:  

I ran 3 main models :
* Logistic Regression 
* Random Forests 
* Decision Trees

Logistic Regression:

This is the most common binary classifier and is quite effective in most cases. 
We get an accuracy of 81.52%. This is a very strong score relative to the baseline of 54%.
The data is standardized before the model is fit. This method is the most simple for classification models and a reason why it's quite effective. 
Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image12.png)




Decision Trees: 

For the decision tree we get a weaker score but still better than the baseline accuracy. This model uses trees to classify the outcome.  The model score is 62.45% which is still an improvement over the baseline of 54%. However it is still fairly weak. It's hard to say why the score is weaker than the logistic regression; maybe because it simplifies the relationships between features more than logistic regression. 
Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image3.png)


![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image6.png)

Below is a diagram of a decison tree. 
![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/Capturedfdfdfdfdf.PNG)

Random Forests:

Similar to the decision tree the random forests also give us a score weaker than the logistic regression. Generally random forests perform in a similar way to the decision tree. OS may not improve especially in data like this. 
Below is the confusion matrix as well as the various scores such as the precision, recall, and f-1 score. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image15.png)
![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image2.png)




However, the random forests help us calculate the feature importance to see which features are the most impactful for calculating the shot outcome. This is the best part of it.





# Feature importance:
This is great in understanding the importance factors for shot outcome. It's clear that shot distance and shot type are major factors followed by the assisters and seconds left. 

![Alt Text](https://github.com/durgesh-plum/NBA-Shot-Predictor/blob/main/image9.png)



# Conclusion:

* The Logistic Regression model performs the best at predicting the Outcome with an accuracy score of 81%. A strong improvement over the baseline(54%). 
* The other two models, Random forests and Decision Trees are not as good but still better than baseline at approximately 61/62%.
* Other models like SVM,XGBoost were tried but not so great. 
* All the models show no signs of overfitting/underfitting. They are accurate. 
* Shot Distance and Shot Type are the major factors influencing shot outcomes. Followed by Assisters.  




# Key Takeaways and Moving Forward: 

* Understanding the Data Science Workflow which follows the data collection, exploration, modeling and predictions. Many aspects of  the data science toolbox were implemented such as Python, Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib and Machine Learning Algorithms.  
* I understood the problem of overfitting/underfitting the data. This was rectified. 
* The importance of a solid dataset is vital for the success of a model. The models that may not have enough features/variables because of a bad dataset will not prove useful. 
* I could have used a shot log dataset over a play by play-by-play dataset. There could be more variables that may help in predicting target (ShotOutcome) better.
* Adding more seasons and increasing the size of the dataset. This would be more representative of the players. 
* Working on improving scores in Random Forests/Decision Trees. These scores were underwhelming compared to Logistic Regression. 
* Applying other models as well, XgBoost, k-NN. These are other classification models that are known for their high accuracy scores especially Xgboost. 
* Spend less time doing EDA, more time modeling. 
* Creating a recommendation system based on players. Recommend shots type + distance. This could provide a nice service for anyone who is interested in understanding the best way to learn about the players
* Use a shot log dataset that helps create a more accurate model. 

