# Rocket Case Study

## Summary

### Problem definition:

The [data set from UC Irvine’s Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing) includes direct marketing campaigns (i.e. phone calls) of a Portuguese banking institution. The goal is to predict if the client will subscribe a term deposit (indicated in the y variable). The task is to create a model that will help this banking institution determine, in advance, clients who will be receptive to such marketing campaigns. Clearly state the metric used for this problem.

### Steps taken:
1. EDA (include link)
2. ...

### Metric
The metric used to evaluate the performance for this problem is the AUC-ROC, or Area Under the Curve of the Receive Operating Characteristic.

*why?*

Because the target variable is imbalanced, if we used a simple accuracy metric, any random model would give us a high score of accuracy. Therefore we use the AUC-ROC metric, which looks at both the True Positive Rate and the False Positive Rate.

### Results
