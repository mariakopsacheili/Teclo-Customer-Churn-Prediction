# Telco-Customer-Churn-Prediction

# Introduction

Telco, a leading telecommunications company established in 2000, delivers a wide range of services, including mobile and landline communications, high-speed Internet (broadband, fiber, and wireless), TV and streaming entertainment, and online security solutions.

The company assigned me the task of developing a machine learning-based churn prediction model using historical customer data. The goal is to identify at-risk customers and enable the marketing team to design targeted retention strategies, ultimately reducing attrition and improving customer loyalty.

# Objectives

- EDA & Data Cleaning: handle missing values, duplicates, outliers and uncover patterns, correlations, and distributions.
	- Conclusions: 
		- tenure column is highly correlated with total charges (0.83). Highly correlated features can reduce model performance and interpretability.
		- my dataset is unbalanced.
		- null values where new customers and they where only 11 so I dropped them out.


- Feature Engineering: Transform categorical features to 0 or 1 or use one-hot encoding form in order my algorithm to understand.

- Model Development: 
	- Split my dataset in features and target and train and test set.
	- Scaling: If the features are on different scales, the algorithm might give more importance to features with larger magnitudes, which can lead to worse performance.
	- Model Evaluation: 
		- Accuracy: measures the ratio of correctly predicted instances (both true positives and true negatives) to the total number of instances.
		- Precision: measures the ratio of correctly predicted positive instances (true positives) to the total number of instances predicted as positive (true positives + false positives).
		- Recall: measures the ratio of correctly predicted positive instances (true positives) to the total number of ***actual*** positive instances (true positives + false negatives).
		- F1 score: the harmonic mean of precision and recall. It balances both metrics and is useful when we want to consider both false positives and false negatives.

	What interests the company the most is to detect all the churns. We don't want to lose any churn. 

	If my model predict a no churn customer is not that important as to miss a churn risk. 

	So, we should focus on False Negative and True Positive. We don't care so much for the False Positive and True Negative. 

	So, the best metric for this occasion is the Recall because, our goal is to minimize false negatives (i.e., we don’t want to miss any true positives). ***False negatives are costly!***
	
	- 1st try: used a basic random forest model. The outcome was a good prediction on the 0 class and a bad prediction on the 1 class. This means that when we are predicting 0 we are almost always correct. This usually happens when a dataset is unbalanced and the models learns to predict always the class that is found the most in the data. 
	- Balance my dataset: downsized the dataset.
	- Split and Scaling again.
	- 2nd try: tested basic models of the algorithms random forest, XGBoost, Logistic Regression, SVMs, LightGBM and checked which one performed better. Logstic Regression had the best performance so I decided to work on this algorithm.  Now, prediction for 0 class was really close to prediction for 1 class.
	- Checked feature importance
	- 3rd try: Created a dataset that contained only the top 10 features to check how my model will perform to this adjustment. Recall for both 0 and 1 predictions is very close to the recall when all 40 features were included. So we prefer this model because it is only using 10 features and brings us a very similar recall.
	- Grid Search: didn't help the model to improve more.
	- Tried to remove the tenure column that was highly correlated with the total charges. No improve.

- Conclusion: Best performed model was Logistic Regression with a Recall of 0.71 for the class 0 (no churn) and 0.79 for class 1 (churn) and an accuracy of 0.75.


