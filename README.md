# Mammogram predictive modelling

Kyeongsoo Kim January 2018 ~ March 2018
## 1. Introduction
Mammography is the most effective method for breast cancer screening 
available today. However, the low positive predictive value of breast 
biopsy resulting from mammogram interpretation leads to approximately 
70% unnecessary biopsies with benign outcomes. 




I used the "mammographic masses" public dataset from the UCI repository (source: https://archive.ics.uci.edu/ml/datasets/Mammographic+Mass)

This data set can be used to predict the severity (benign or malignant) 
of a mammographic mass lesion from BI-RADS attributes and the patient's age. It contains 961 instances of masses detected in mammograms, and contains the following attributes:
```
1. BI-RADS assessment: 1 to 5 (ordinal)
2. Age: patient's age in years (integer)
3. Shape: mass shape: round=1 oval=2 lobular=3 irregular=4 (nominal)
4. Margin: mass margin: circumscribed=1 microlobulated=2 obscured=3 ill-defined=4 spiculated=5 (nominal)
5. Density: mass density high=1 iso=2 low=3 fat-containing=4 (ordinal)
6. Severity: benign=0 or malignant=1 (binominal)
```



BI-RADS is an assesment of how confident the severity classification is; it is not a "predictive" attribute and so we will discard it. The age, shape, margin, and density attributes are the features that we will build our model with, and "severity" is the classification we will attempt to predict based on those attributes.

Although "shape" and "margin" are nominal data types, which sklearn typically doesn't deal with well, they are close enough to ordinal that we shouldn't just discard them. The "shape" for example is ordered increasingly from round to irregular.

A lot of unnecessary anguish and surgery arises from false positives arising from mammogram results. If we can build a better way to interpret them through supervised machine learning, it could improve a lot of lives.


## 2. Project Details
I applied several different supervised machine learning techniques to this data set, and found the best model by checking which one yields the highest accuracy as measured with K-Fold cross validation (K=10). 

The machine learning techniques I applied are as follows:

```
Decision tree
Random forest
KNN
Naive Bayes
SVM
Logistic Regression
a neural network using Keras
```


## 3. Accuracy Comparision and Analysis
Decision tree.

    0.777108
    train_size=0.75, test_size=0.25

K-Fold cross validation (k = 10)

    0.737355
    Slightly improved from Decision tree.
Random forest

    0.754049
    Compared to Decsion tree, improved by 0.018472 

SVM

    when kernel='rbf'
        * 0.801202 (Second Highest performance)
    when kernel='linear'
        * 0.796498
    when kernel='poly'
        * 0.792753
    when kernel='sigmoid'
        * 0.735105


Naive Bayes

    0.784405

KNN (k = 7)

    0.794059
Logistic Regression

    0.807358 (Highest performance)


Logistic Regression yeilds the best performance, which is a simple way to tackling this sort of thing compared to all the other fancy techniques.

Since this is fundamentally just a binary classification problem, Logisitic Regression still qualify the proper model of the problem. 

## 4. Conclusion 
Some other algorithms could be also tuned to produce comparable results with 79-80% accuracy, However Logistic Regression produced the best performance.

