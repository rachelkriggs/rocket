# Rocket Case Study

## Summary

### Problem definition:

The [data set from UC Irvine’s Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing) includes direct marketing campaigns (i.e. phone calls) of a Portuguese banking institution. The goal is to predict if the client will subscribe a term deposit (indicated in the y variable). The task is to create a model that will help this banking institution determine, in advance, clients who will be receptive to such marketing campaigns. Clearly state the metric used for this problem.

### Steps taken:
1. [EDA](https://github.com/rachelkriggs/rocket/blob/main/Rmd/bank_EDA.md)
  - checked for missing values
  - checked for duplicate rows
  - checked for imbalance of target variable
  - looked for potential outliers
  - checked for correlated features

2. Split the data into train, validation, and test sets
  - using a 70/15/15 split
  - also removed duplicate rows

3. Pre-processed the data
  - Converted target variable to numeric & binary
  - One-hot encoded categorical variables
  - Dropped some features

### Metric
The metric used to evaluate the performance for this problem is the AUC-ROC, or Area Under the Curve of the Receive Operating Characteristic.

*why?*

Because the target variable is imbalanced, if we used a simple accuracy metric, any random model would give us a high score of accuracy. Therefore we use the AUC-ROC metric, which looks at both the True Positive Rate and the False Positive Rate.

### Results
