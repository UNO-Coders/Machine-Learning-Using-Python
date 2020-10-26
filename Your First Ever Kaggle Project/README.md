### Kaggle's Titanic Machine Learning Problem is one of the easiest project to start your Journey towards Machine learning. 
### Follow along with the Notebook.

## About The Compitition
We all know about legendary movie **Titanic**,that romatic story is unfortunately fictional, but the disaster was real.
On April 15, 1912, the widely considered “unsinkable” RMS Titanic sank after colliding with an iceberg. Unfortunately, there weren’t enough lifeboats for everyone onboard, resulting in the death of 1502 out of 2224 passengers and crew.
While there was some element of luck involved in surviving, it seems some groups of people were more likely to survive than others.
Kaggle provides us train and test data sets, which containts details like **Sex,Age,Passenger Class,Embarked etc**,.Our job is to find who had survived in test data set.


## Brief Overview
In data set there are **missing values**, some hidden but important features like name **Prefix,Family Size**,which plays good role predicting person's survive chance,
we imputed missing values with **Random Forest Regressor** which is way more accurate than filling with **Mean,Median or most frequent value(Mode)**.
Then we used different models and tune them and pick the best model for our final prediction.
```sh
df.isna().sum()
```
```sh
PassengerId      0
Survived       418
Pclass           0
Sex              0
Age            263
SibSp            0
Parch            0
Ticket           0
Fare             1
Embarked         2
```
**Filling Fare with median value 'cause there is too many outliers to affect our mean**
<div>
    <a href="https://plotly.com/~Aditya1112/1/?share_key=XvEsaVIjQk5BfDfei4pvWg" target="_blank" title="box" style="display: block; text-align: center;"><img src="https://plotly.com/~Aditya1112/1.png?share_key=XvEsaVIjQk5BfDfei4pvWg" alt="click to redirect" style="max-width: 100%;width: 800px;"  width="800" onerror="this.onerror=null;this.src='https://plotly.com/404.png';" /></a>
</div>

**Family Size,Name Prefix and Their Survive Chance**

![FamSize-Survive](Graphs/familysize.png)   ![Prefix-Survive](Graphs/prefix.png)

**Family Size with 2,3 and 4 had higher chance of Survive,**

**Similarly,prefix Mr[Married Man :(  ] had very low chance of Survive**

**Tuning Diffrent model and predict the future with best model**

KNN model's accuracy over K values
<div>
    <a href="https://plotly.com/~Aditya1112/3/?share_key=ELO7dxrEVylMHSaYk1tPKp" target="_blank" title="knn_lie" style="display: block; text-align: center;"><img src="https://plotly.com/~Aditya1112/3.png?share_key=ELO7dxrEVylMHSaYk1tPKp" alt="knn_line" style="max-width: 100%;width: 700px;"  width="700" onerror="this.onerror=null;this.src='https://plotly.com/404.png';" /></a>
</div>

After some try and error **Random Forest** stand out
```sh
confusion_matrix(y_test,y_pred_rfc)
```
Output:
```sh
array([[268,   5],
       [  2, 171]])
```
**Feature Importance**:
![feature-importance](Graphs/rf_feature_importance.png)

Prefix Mr,Sex_male and Passenger Class are **Highly correlate** to Wheather pearson survive or not.

For Deployment check the original Repo
[Here](https://github.com/Aditya-Rajgor/Personal-Projects/edit/master/Titanic ML Problem)


[<img src="https://cdn.worldvectorlogo.com/logos/heroku.svg" width="100" height="64" />][heroku-url]
[heroku-url]: https://titanic101.herokuapp.com/
