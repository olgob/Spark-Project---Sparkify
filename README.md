# Spark Project - Sparkify

### Summary of the project

In this project I manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn. I use Spark to build machine learning models with large datasets, far beyond what could be done with non-distributed technologies like scikit-learn.

### Motivation for the project

Predicting churn rates is a challenging and common problem that data scientists and analysts regularly encounter in any customer-facing business. Additionally, the ability to efficiently manipulate large datasets with Spark is one of the highest-demand skills in the field of data.

### Libraries used on this project

# necessary if we use pyspark on a local machine

- pyspark
- numpy
- pandas
- matplotlib
- datetime


### Explanation of the files in the repository

<pre>
.
├── article pictures ----------------------- contain the plots pictures and screenshots used for the blog post written on medium.
│sparklify_features_exploration.ipynb ------ notebook containing the code to load data and study different features for predicting churn.
│sparklify_machine_learning_model.ipynb ---- notebook containing the code to load data, build machine learning model with selected features using gridsearch and crossvalidation on a train dataset and get the results of the predicitons on a test dataset

</pre>

### Summary of the results of the analysis

After loading and cleaning the data, we figured out in the "sparklify_features_exploration" notebook that the following features were relevant to distinguish users that churn from those who don't:
- n_friends : the number of friend of the users
- r_nextsong_session : The average ratio of songs /sessions
- r_roll_advert_song : The average ratio of advertisement / song
- r_about_session : The average ratio of about page / session
- r_error_session : The average ratio of error page / session
- r_thumbs_down_song : The average ratio of thumbs down / song
- gender : The gender of the users
- level : The level of subscription of the users
- avg_diff_days : The average days difference between two successive sessions

We use pyspark then to load, clean data, and prepare the different features. We then study the performance of 4 models to predict users who churn from those who don't :
- Logistic regression
- Decision tree classifier
- Random forest classifier
- Gradient-boosted tree classifier

After having training the models with grid search and 5-folds cross validation on the 4 models using a training dataset, we test the model on a test dataset that haven't seen before by the models and optain the following results for the classification :

|Model                             | accuracy |  precision |  recall  |    f1    |
|----------------------------------|----------|------------|----------|----------|
| Logistic regression              | 0.764706 |  0.5       |  0.25    | 0.333333 |
| Decision Tree Classifier         | 0.823529 |  0.625     |  0.625   | 0.625    |
| Random forest classifier         | 0.794118 |  1.0       |  0.125   | 0.222222 |
| Gradient-Boosted Tree Classifier | 0.882353 |  0.833333  |  0.625   | 0.714286 |

### Acknowledgements

the dataset mini_sparkify_event_data.json is a 128MB json that exceed the limit size of file on github. It can be found on udacity website in the data scientist nanodegree program.
