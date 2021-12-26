
# Kaggle- Taxi Fare Prediction

The Aim of this of this Project is to work on a (completed) Kaggle challenge on taxi fare prediction. 

Please visit https://www.kaggle.com/c/new-york-city-taxi-fare-prediction to know more about this
problem, and download the data.

This project can be categorized into two main components:

    1. Processing the data and EDA(Exploratory data analysis)
    2. Modelling and making Predictions 

#### Note

As the dataset is really huge(55M rows), we will be using only 2M rows for training our models and making Predictions

## Dataset

Get the training and test data from https://www.kaggle.com/c/new-york-city-taxi-fare-prediction
## Result and Analysis

### Modelling and Top 2 Scores(using 2 Million data rows):

#### 1st Top Score(RMSE): 3.08537
Using LightGBM with params : {'objective': 'regression', 'boosting': 'gbdt', 'reg_sqrt': True, 'learning_rate': 0.03, 'num_leaves': 1200, 'max_depth': -1, 'max_bin': 500, 'num_rounds': 500, 'early_stopping_round': 10, 'metric': 'rmse', 'force_row_wise': True}

#### Reason why it performed well compared to other models:
LightGBM is a histogram based algorithm that buckets the continuous feature values into discrete bins which helps reduce the training time. It provides better accuracy than any other
boosting method and goes neck to neck with XGBoost but is way faster than XGBoost, that’s why I decided to go with it. It does leaf wise split approach rather than level-wise which is one of the factors in getting good accuracy. But, it could lead to overfitting which could be avoided by enabling the max_depth parameter. Another reason of picking it being it works really well with large datasets which was the case here.

#### 2nd Top Score(RMSE): 3.13135
Using XGBoost Regressor with params: {n_estimators = 100, max_depth = 9}

#### Reason why it performed well compared to other models:
Reason for such a good score being it is proven to push the limits of computing power of boosted tree algorithms and often used for winning various Kaggle Competitions. It is build for the sole purpose of best performance and speed. This comes under ensemble methods where we create a strong classifier based on weak classifiers. It has many regularization parameters which also helps to prevent overfitting.

#### Other Models(which didn’t work as well): In addition to the above two mentioned, I have also used Decision Trees, Random Forests, Gradient Boost etc. But they didn’t give such good results, reasons are as follows:
    1. Decision Tree: Not performance oriented. Gives a really low score and could overfit if max_depth is not properly tuned.

    2. Random Forests: Better accuracy than decision trees, but for such a large dataset it is not recommended since it takes forever to train and the score is also not upto the mark compared to LGBM and XGBoost.

    3. Gradient Boost: Better accuracy than both mentioned above and speed is also good but better techniques are available that can leverage the potential of Gradient Boost to the next level like Extreme Gradient Boost or XGBoost.


### Note : 

I have also tried LGBM with 5 Million data rows which gave me a RMSE of 2.99722. Reason for not including it on the top score being it takes a lot of time to fully train.


## Authors

- [@AyanPahari](https://github.com/AyanPahari)

