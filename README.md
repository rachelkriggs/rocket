# Rocket Case Study

## Summary

### Problem definition:

The [data set from UC Irvine’s Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing) includes direct marketing campaigns (i.e. phone calls) of a Portuguese banking institution. The goal is to predict if the client will subscribe a term deposit (indicated in the y variable). The task is to create a model that will help this banking institution determine, in advance, clients who will be receptive to such marketing campaigns. Clearly state the metric used for this problem.

### Steps taken:
1. [Exploratory Data Analysis](https://github.com/rachelkriggs/rocket/blob/main/Rmd/bank_EDA.md)
    - checked for missing values
    - checked for duplicate rows
    - checked for imbalance of target variable
    - looked for potential outliers
    - checked for correlated features

2. [Split the data into train, validation, and test sets](https://github.com/rachelkriggs/rocket/blob/main/notebooks/01_split.ipynb)
    - using a 70/15/15 split
    - also removed duplicate rows

3. [Pre-process the data](https://github.com/rachelkriggs/rocket/blob/main/notebooks/02_process.ipynb)
    - Converted target variable to numeric & binary
    - One-hot encoded categorical variables
    - Dropped some features

4. Models
    - [Create a baseline model and experiment with several models using default parameters](https://github.com/rachelkriggs/rocket/blob/main/notebooks/03_model.ipynb)
    - [Tune hyperparameters of select models](https://github.com/rachelkriggs/rocket/blob/main/notebooks/04_tune.ipynb)
    - [Run the models on the held-out test set](https://github.com/rachelkriggs/rocket/blob/main/notebooks/05_test.ipynb)

### Metric
The metric used to evaluate the performance for this problem is the AUC-ROC, or Area Under the Curve of the Receive Operating Characteristic.

*why?*

Because the target variable is imbalanced, if we used a simple accuracy metric, any random model would give us a high score of accuracy. Therefore we use the AUC-ROC metric, which looks at both the True Positive Rate and the False Positive Rate.

See the [scikit-learn documentation on ROC](https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics).

### Results

| model | Train ROC-AUC score | Validation ROC-AUC score | Test ROC-AUC score |
| ----- | ------------------- | ------------------------ | ------------------ |
| Logistic Regression | 0.801587 | 0.791295 | 0.773089 |
| LightGBM | 0.836647 | 0.803069 | 0.780498 |
| XGBoost | 0.854777 | 0.807432 | 0.782537 |
| Random Forest | 0.875211 | 0.805114 | 0.779984 |

- The Random Forest model is not the best model of this group. It doesn't have the highest test score, and it overfits the most.
- It's debatable which of the remaining 3 models could be considered the best one. While XGBoost has the highest test score, it also overfits more than LightGBM or Logistic Regression.


### Ideas for further work
- deal with correlated columns (by applying PCA, dropping features, or some other method)
- deal with the '999' value in the `pdays` column (for now this was left as is)
- deal with class imbalance in the target variable
  - by oversampling: create copies of the minority class so we have the same number of training examples in each class
  - not enough data to undersample
- further engineer features
- further tune models
