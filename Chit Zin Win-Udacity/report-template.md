# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Chit Zin Win

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: Some predicted values are negative and are needed to set them zero before submitting to kaggle.
### What was the top ranked model that performed?
TODO: "Predictor_with_new_feature" model named "WeightedEnsemble_L3" with best kaggle score "0.51763" on test data

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: I plot the correlation heatmap to analyze "leaky" and "multicollinearity". Then I found "temp" and "atemp" have multicollinearity and To reduce multicollinearity, we need to drop a column which is less correlated with the target value "count".

"Casual" and "Register" have high correlation with target. Therfore, we drop them while training model for "leaky error".

I separated "datetime" data into hour, day, or month parts for better understanding of renting patterns according to each day and hour durations. Then I dropped the origin "datetime" column.

"season" and "weather" are actually "category" datatype but they are described as "int64". Therefore, I changed their datatype to "category".

### How much better did your model preform after adding additional features and why do you think that is?
TODO: Nearly 70% better than the initial model as (1.79544-0.51763) = nearly 1.28. (score of initial model as a baseline)

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: About 55% better as (1.79544-.82784) = nearly 1) (score of initial model as a baseline)

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: Spend more time on "Hyper parameter tuning" as I want to see how AutoGluon performs with other hyperparameters.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
model	hpo1	hpo2	hpo3	score
0	initial	default_values	default_valuesdefault_valuesdefault_valuesdefa...	default_valuesdefault_valuesdefault_valuesdefa...	1.79544
1	add_features	default_values	default_valuesdefault_values	default_valuesdefault_valuesdefault_values	0.51763
2	hpo	NN_TORCH	GBM	KNN	0.82784



### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
TODO: Add your explanation
-AutoGluon's performance highly depends on the time_limit. If I set higher number, then the model will get more time to find a better solution overall.