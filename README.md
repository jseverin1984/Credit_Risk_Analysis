# Credit Risk Analysis

## Overview

For this analysis, I was asked to evaluate credit card credit data from LendingClub. I was tasked to predict if someone, based off of a
specific feature set, would fall into the high credit risk or low credit risk category. The goal would be to help LendingClub make better
decisions when approving of denying credit.  I will be using three different methods to resample the data in order to provide better
predictive outcomes.  I will use Random Over Sampling, SMOTE, and Cluster Centroid algorithms to resample the data, then use logistic
regression machine learning to train the resampled data. Lastly, I will run fresh data through the trained algorithm and use quantitative
measures to compare the three resampling techniques for their ability to provide a more accurate prediction alogrithm. I will also try
two more machine learning models, Balanced Random Forest Classifier and Easy Ensemble Classifier, to see if they can provide a better
prediction model.

## Results

Note to grader.  I decided to use the stratify parameter when using the train_test_split class from sklearn.  With having two classes and
one being greatly skewed larger than the other, I wanted to stratify my splits in order to have potentially better outcomes. Since I used
the stratify parameter, my numbers have come out slightly different than what was shown in the starter ipynb's.

A couple definitions to help understand the metrics shown in the images.

- Balanced accuracy score
	The percentage of correctly predicted observations by the model.
- Precision
	How reliable a models prediction is. For example, if a model to predict diabetes predicts I have diabetes, how likely is it that
	the prediction is correct. This is scored from zero to one. The closer to one the better the prediction.
- Recall/sensitivity
	The ability of a model to find all of the true positives within the dataset. For example, I already know that I have diabetes,
	so how likely will the model accurately predict that I have diabetes. This is scored from zero to one. The closer to one the better the prediction.

![random oversampling](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/random_over_sampling.png)
- Balanced accuracy score: 64%
- Precision for high risk: .01
- Precision for low risk: 1.0
- Recall for high risk: .62
- Recall for low risk: .67

![smote oversampling](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/smote_oversampling.png)
- Balanced accuracy score: 65%
- Precision for high risk: .01
- Precision for low risk: 1.0
- Recall for high risk: .66
- Recall for low risk: .64

![cluster centroid undersampling](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/cluster_centroid.png)
- Balanced accuracy score: 51%
- Precision for high risk: .01
- Precision for low risk: 1.0
- Recall for high risk: .63
- Recall for low risk: .39

![smoteenn under/oversampling](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/smoteenn.png)
- Balanced accuracy score: 62%
- Precision for high risk: .01
- Precision for low risk: 1.0
- Recall for high risk: .70
- Recall for low risk: .55

![balanced random forest](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/balanced_random_forest.png)
- Balanced accuracy score: 79%
- Precision for high risk: .04
- Precision for low risk: 1.0
- Recall for high risk: .67
- Recall for low risk: .91

![easy ensemble](https://github.com/jseverin1984/Credit_Risk_Analysis/blob/main/Resources/easy_ensemble.png)
- Balanced accuracy score: 93%
- Precision for high risk: .07
- Precision for low risk: 1.0
- Recall for high risk: .91
- Recall for low risk: .94

## Summary

I ran a logistic regression model on data that was not resampled and obtained a balanced accuracy score of 50%. When using oversampling techniques
on the data to resample it before training the model with the new data, provided an average increase of 14.5% in the balanced accuracy score.
While undersampling showed no improvement at all.  Both classifier models greatly increased the balanced accuracy score, and the easy ensemble
had over scores over .9 for recall.

I would not recommend any of these models to be used as the sole source of determining if someone would be high or low risk for credit eligibility.
Every model allows far too many false positives when predicting high risk credit.  This would cause an incredibly high portion of people to not be
able to get credit, even though in reality, they are a low credit risk. Out of the 87 people who were high risk, the easy ensemble model did flag
91% of them as high risk. But it also flagged 979 people as high risk, who are actually low risk.  So even with such a high recall on high risk
predictions, I do not believe its worth it when so many people are getting a false positive for being high risk.