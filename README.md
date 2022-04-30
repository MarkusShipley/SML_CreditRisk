# Supervised Machine Learning Homework - Predicting Credit Risk

In this assignment, you will be building a machine learning model that attempts to predict whether a loan from LendingClub will become high risk or not. 

## Background

LendingClub is a peer-to-peer lending services company that allows individual investors to partially fund personal loans as well as buy and sell notes backing the loans on a secondary market. LendingClub offers their previous data through an API.

You will be using this data to create machine learning models to classify the risk level of given loans. Specifically, you will be comparing the Logistic Regression model and Random Forest Classifier.

## Instructions

### Retrieve the data

In the `Generator` folder in `Resources`, there is a [GenerateData.ipynb](/Resources/Generator/GenerateData.ipynb) notebook that will download data from LendingClub and output two CSVs: 

* `2019loans.csv`
* `2020Q1loans.csv`

You will be using an entire year's worth of data (2019) to predict the credit risk of loans from the first quarter of the next year (2020).

Note: these two CSVs have been undersampled to give an even number of high risk and low risk loans. In the original dataset, only 2.2% of loans are categorized as high risk. To get a truly accurate model, special techniques need to be used on imbalanced data. Undersampling is one of those techniques. Oversampling and SMOTE (Synthetic Minority Over-sampling Technique) are other techniques that are also used.

## Preprocessing: Convert categorical data to numeric

Create a training set from the 2019 loans using `pd.get_dummies()` to convert the categorical data to numeric columns. Similarly, create a testing set from the 2020 loans, also using `pd.get_dummies()`. Note! There are categories in the 2019 loans that do not exist in the testing set. If you fit a model to the training set and try to score it on the testing set as is, you will get an error. You need to use code to fill in the missing categories in the testing set. 

## Consider the models

You will be creating and comparing two models on this data: a logistic regression, and a random forests classifier. Before you create, fit, and score the models, make a prediction as to which model you think will perform better. You do not need to be correct! Write down (in markdown cells in your Jupyter Notebook or in a separate document) your prediction, and provide justification for your educated guess.

CONSIDER THE MODELS - MAKING PREDICTIONS
Great article/post that helps explain the differences between linear regression,�
https://scikit-learn.org/stable/auto_examples/calibration/plot_compare_calibration.html?highlight=logistics%20regression
https://towardsdatascience.com/logistic-regression-detailed-overview-46c4da4303bc�
https://towardsdatascience.com/understanding-random-forest-58381e0602d2

"The random forest is a classification algorithm consisting of many decisions trees. It uses bagging and feature randomness when building each individual tree to try to create an uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree." - Tony Yiu
"No algorithm that trains its model is immune to overfit. (That which is considered noise in one problem could be considered signal in another problem, so only a magical algorithm could always discern what the user wants.) A Random Forest with few trees is quite prone to overfit to noise. This is easily demonstrated because RF with just one tree is the same as a single tree. As more trees are added, the tendency to overfit generally decreases. It never, however, approaches zero. No number of trees will ever remove overfit. The RF page here on Wikipedia gives a visual demonstration of this behavior. It is also well documented in published literature. Segal et al. showed that Brieman's choice of datasets lacked significant noise, and that RF does in fact overfit (http://escholarship.org/uc/item/35x3v9t4.pdf). Gashler et al. showed empirically that Random Forest does not handle noise injected into arbitrary datasets as well as entropy-reducing decision trees (http://axon.cs.byu.edu/papers/gashler2008icmla.pdf). This is precisely because RF overfits to the noise, whereas the entropy-reducing trees overfit less. The method of randomly choosing divisions is inherently more susceptible to overfit because it gives equal probability to all attributes. Breiman has a conflict-of-interest in promoting RF, and repeatable experiments show that he is wrong to suggest that RF never overfits. Further, the notion of an algorithm that does not overfit is absurd in context of the No Free Lunchn Theorem. Adding more trees to the ensemble does in fact reduce variance, but it does not correct any bias. Please stop repeating Breiman's false marketing efforts.--Headlessplatter (talk) 13:45, 28 August 2012 (UTC)" -�https://en.wikipedia.org/wiki/Talk%3ARandom_forest#:~:text=January%202012%20(UTC)-,Overfitting,stay%20in%20a%20certain%20value.
https://carpentries-incubator.github.io/ml4bio-workshop/04-trees-overfitting/index.html

PREDICTION: In order to make my best guess at which model would perform better, I researched and read the above referenced articles. Decision trees are prone to overfitting. With overfitting, we have a risk that learning is not occuring when the test data is appled to the model but instead the result rendered is the equivalnet of "memorization."
Based on my review of the data and researching of the two models, I believe the logistics regression model is the best model for our data. I am concerned about the risk of overfitting the model with this dsta set. Based on Yiu's comment regarding random forest and its use of bagging in an attempt to create an uncorrelated forest of trees, I don't believe random forest is the best model for this data.


## Fit a LogisticRegression model and RandomForestClassifier model

Create a LogisticRegression model, fit it to the data, and print the model's score. Do the same for a RandomForestClassifier. You may choose any starting hyperparameters you like. Which model performed better? How does that compare to your prediction? Write down your results and thoughts.

## Revisit the Preprocessing: Scale the data

The data going into these models was never scaled, an important step in preprocessing. Use `StandardScaler` to scale the training and testing sets. Before re-fitting the LogisticRegression and RandomForestClassifier models on the scaled data, make another prediction about how you think scaling will affect the accuracy of the models. Write your predictions down and provide justification.

Fit and score the LogisticRegression and RandomForestClassifier models on the scaled data. How do the model scores compare to each other, and to the previous results on unscaled data? How does this compare to your 
prediction? Write down your results and thoughts.

##CONCLUSION

CONCLUSION: With logisitics regression, we see and increase from 51% to 76% with scaling.  This implies that the attributes that were not scaled played a bigger impact with the logistics regression model than with the Random Forest Classifier.  HOWEVER, I did print out the scores for the each of the train sets as well.  Both the scaled and non-scaled Random Forest Classifier's Train score is 1.0 which means that the model is overfit -- basically it is not learning, it's memorized and spitting out the result. 

## Rubric

[Unit 19 - Supervised Machine Learning Homework Rubric](https://docs.google.com/document/d/1f_eN3TYiGqlaWL9Utk5U-P491OeWqFSiv7FIlI_d4_U/edit?usp=sharing)

### References

LendingClub (2019-2020) _Loan Stats_. Retrieved from: [https://resources.lendingclub.com/](https://resources.lendingclub.com/)

- - -

© 2021 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
