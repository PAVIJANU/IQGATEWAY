![image](https://github.com/PAVIJANU/IQGATEWAY/assets/127427914/0104031e-f09a-4c15-9be8-4e8861f34c76)
cv.py:
- This file contains the implementation of the NestedCV class for nested time series cross-validation.
- The class is tested with unit tests to ensure its functionality.

model.ipynb:
- This Jupyter notebook demonstrates the usage of the NestedCV class to evaluate a linear regression model.
- It loads a dataset, initializes NestedCV with 3 folds, and evaluates the model using nested cross-validation.

What is Cross-Validation?
Before diving into nested CV, let’s understand the basics of cross-validation. Cross-validation is a technique used to evaluate the predictive performance of a statistical model. It divides the dataset into a fixed number of folds or subsets. The model is trained on the combination of these folds except one, which is used as the test set. This process repeats so that each fold serves as the test set exactly once, allowing every data point to be used for both training and testing.

Why Nested Cross-Validation?
In a standard cross-validation setup, you might tune hyperparameters using the same data that measures model performance. This can lead to overly optimistic estimates of the model’s generalization error because the model has indirectly “seen” the test data during hyperparameter tuning, aka, data leakage. Nested cross-validation addresses this issue by separating the data used for hyperparameter tuning from the data used for performance evaluation.
