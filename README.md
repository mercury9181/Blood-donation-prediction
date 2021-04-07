# Blood-donation-prediction


## Dataset: 
The dataset, obtained from the UCI Machine Learning Repository, consists of a random sample of 748 donors. The data set contains 4 columns. They are:
R (Recency - months since the last donation)
F (Frequency - total number of donation)
M (Monetary - total blood donated in c.c.)
T (Time - months since the first donation)
a binary variable representing whether he/she donated blood in March 2007 (1 stand for donating blood; 0 stands for not donating blood

## Objective: 
The objective is to predict if a blood donor will donate within a given time window.


## Insight on the dataset: 
From the class distribution of the dataset it is seen that 
0 class has: 570 data samples (approx. 76%)
1 class has: 178 data samples (approx. 26%)
From this, it is clear that the dataset suffers from a class imbalance problem. As we can see there is a class imbalance problem is present on the dataset, AUC would be an indicator of a better model rather than accuracy.
Also from the var function, it can be noticed that the Monetary (c.c. blood) column suffers from a high variance problem and needs normalization. After dividing the data from the training and test sets, normalization between instances can be performed using data from the training set and testing set. Since the test set represents new, previously unknown data, it is not meant to be available during the training period. This also reduces possible data leakage problems.

## Pre-processing: 
The dataset was divided into 80% training set and 20% test set stratified by the target (column name= “ whether he/she donated blood in March 2007”) to keep the ratio evenly. 
After that log normalization was done on both the test and training set.


## Single model declarations and testing: 
4 models were created and tested on the test set using accuracy and AUC. 
logistic regression. (Performed best)
Support Vector Classification
Naive Bayes classification
Random forest classification
 
## Create a Voting classifier(Soft) and test: 
A voting classifier is an ensemble learning technique where it takes multiple models and output prediction after taking into account each model’s predictions. There are two types of voting classifier:
Soft: In a soft voting classifier, it takes the probabilistic outcome of each model to predict the final class.
Hard: In the case of a hard voting classifier, every classifier will output 0 or 1 and only the highest voted member will be chosen by the voting classifier.
	For example, let’s say there are 3 classifiers and their probabilistic outputs are,
	0.45 , 0.48, 0.99
In the case of hard voting, the output will be  (0,0, 1). So, the voting classifier will choose  0(False). 
But in the case of soft voting, the output will be probabilistic 0.64 ( (0.45+0.45+0.99)/3 = 0.64) which means positive.

In this problem, soft voting was chosen as the probabilistic outcome is needed to calculate the AUC score.

The soft Voting classifier achieved 0.78 accuracies and a 0.75 AUC score.


	
## Future work: 
Use grid-search CV or randomized search CV with ensemble model to see if performances can be more tuned or not.
