Bike-sharing demand is highly relevant to related problems companies encounter, such as Uber, Lyft, and DoorDash. Predicting demand not only helps businesses prepare for spikes in their services but also improves customer experience by limiting delays. In this project, we used the AutoGluon(opens in a new tab) library to train several models for the Bike Sharing Demand(opens in a new tab) competition in Kaggle. By using Tabular Prediction(opens in a new tab) to fit data from CSV files provided by the competition. This project demonstrated the use AutoGluon to train several iterations of models and recorded optimization of the problem. We submitted several entries to the competition and achieved a rank within Kaggle.

Deploy powerful models like AutoGluon and other models quickly with AWS SageMaker. We started with loading your data into Pandas, doing exploratory data analysis, training the model, and performing hyperparameter tuning.

## Initial Training
The model did not perform well for the first time because exploratory data analysis and feature engineering were not performed on the dataset.
No negative prediction values are not applicable for submission, so all negative values are set to 0 before submission.
WeightedEnsemble_L3 was the top ranked model.

## Exploratory data analysis and feature creation
Features such as year, month, day, hour were extracted from datetime feature. 
Season and weather features are naturally categorical variables, they were transformed form integer to category data type. 

Comparing to the inital model, the model with additional features improved and gave RMSE score of 33.769 and the best Kaggle score of 0.4775. This is due to the use of categorical variables instead of integeral data types, splitting datatime into multiple features and ignoring casual and registered in training. 

## Hyper parameter tuning
Most of the times, AutoGluon achieves its best performance without hyperparameter tuning and some configurations are useful while other are not. The model of hyper parameters didn't improve regarding to the model of additional features which gave the best results.
I would try more hyperparameter tuning to understand it better.

## A table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|1.80354|
|add_features|default|default|default|0.44775|
|hpo|GBM|dropout_prob: 0.0, 0.5|num_boost_round: 100|0.47635|

## Summary
AutoGluon contains a large family of models and range of hyperparameters. A top-ranked AutoGluon model improved results espically with exploratory data analysis, feature engineering and no hyperparameter tuning. Different hyperparameter of AutoGluon can be tuned wisely to improve performance.
