# Red Wine Quality Analysis
This project aims to determine which chemical features are the best indicators of red wine quality and use the most appropriate method to model the same. Has been implemented using R programming.

## Dataset Used
The [Red Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality) was used. While the original dataset was larger, 1000 samples have been used for this project. It contains a total of 12 variables where 11 are chemical factors potentially affecting the dependent variable, i.e, the quality.

## Statistical Methods Used
1. Correlation Matrix
2. Histograms
3. QQ-plots
4. Simple Linear Regression
5. Multiple Linear Regression
6. Lasso Method (L1 regularization)
7. Random Forest

## Model 1: Simple Linear Regression
Using only 1 predictor variable, i.e, **alcohol** (highest correlation with quality)
<img src="/slr_summary.png" alt="" width="500" height="350"/>
<img src="/slr_graph.png" alt="" width="400" height="350"/>

## Model 2: Multiple Linear Regression
Using the top 4 variables with highest correlation (i.e., **alcohol, volatile.acidity, total.sulfur.dioxide, citric.acid**) to the quality variable.
<img src="/mlr_summary.png" alt="" width="500" height="350"/>
<img src="/mlr_graph.png" alt="" width="400" height="350"/>

## Model 3: Multiple Linear Regression with Lasso Technique
Using the Lasso technique to eliminate the effect of correlation within variables. It aims to shrink coefficients of some features to zero, effectively performing feature selection. <br>
<img src="/mlr_lasso_summary.png" alt="" width="500" height="350"/>
<img src="/mlr_lasso_graph.png" alt="" width="400" height="350"/>

## Model 4: Random Forest
Since there is some degree of imbalance in the data, the Random Forest model could be a good fit. It also helps with feature selection which could handle the problem of correlation between 2 predictors. <br>
<img src="/random_forest_summary.png" alt="" width="500" height="350"/>
<img src="/random_forest_graph.png" alt="" width="400" height="350"/>

## Results
**Model Comparison using various Metrics:**
![Metric Comparison](/metric_comparison.png)

Model 4 (i.e., Random Forest) has the highest R² value and the lowest RMSE (Root Mean Squared Error) values for training, testing and validation data. A higher R² generally implies that the model has good predictive power and explains most of the variability in the target variable. RMSE provides an indication of how well the model's
predictions align with the actual observed values. Hence, we can say that the **Random Forest** model is the best fit for the Red-wine dataset.

It can also be concluded that the most influential features in predicting red-wine quality are: **alcohol, volatile.acidity, total.sulfur.dioxide**. Amongst the top-4 features, **citric.acid** does not contribute much to the model. This is likely due to the high correlation between **volatile.acidity** & **citric.acid**. Multicollinearity occurs when two or more independent variables in the model are highly correlated with each other. This implies that the variables contain redundant information and are not providing unique contributions to the model. Multicollinearity can exacerbate overfitting.
