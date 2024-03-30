
cv.py:
- This file contains the implementation of the NestedCV class for nested time series cross-validation.
- The class is tested with unit tests to ensure its functionality.

model.ipynb:
- This Jupyter notebook demonstrates the usage of the NestedCV class to evaluate a Time series model.
- It loads a dataset, initializes NestedCV with 3 folds, and evaluates the model using nested cross-validation.

**What is Cross-Validation?**
Before diving into nested CV, let’s understand the basics of cross-validation. Cross-validation is a technique used to evaluate the predictive performance of a statistical model. It divides the dataset into a fixed number of folds or subsets. The model is trained on the combination of these folds except one, which is used as the test set. This process repeats so that each fold serves as the test set exactly once, allowing every data point to be used for both training and testing.
![image](https://github.com/PAVIJANU/IQGATEWAY/assets/127427914/0104031e-f09a-4c15-9be8-4e8861f34c76)
In this approach:

The dataset is divided in training, validation and test set
The model is trained using the training fold
Hyperparameters are tested on the validation set
The final performance are evaluated on the test set.

![image](https://github.com/PAVIJANU/IQGATEWAY/assets/127427914/5cb578b8-22e4-4d26-ae07-a9e80311cb0c)


**Why Nested Cross-Validation?**
In a standard cross-validation setup, you might tune hyperparameters using the same data that measures model performance. This can lead to overly optimistic estimates of the model’s generalization error because the model has indirectly “seen” the test data during hyperparameter tuning, aka, data leakage. Nested cross-validation addresses this issue by separating the data used for hyperparameter tuning from the data used for performance evaluation.


**Data leakage happens when information from outside the training dataset is used to create the model, leading to overly optimistic performance estimates.**

![image](https://github.com/PAVIJANU/IQGATEWAY/assets/127427914/4fe927f1-5f84-495f-afa2-3627a26019a1)

**Report: NESTEDCV in Time Series**

**Introduction:**
The following report presents a comprehensive time series analysis of Gazoza sales in Greece using historical data. The analysis encompasses data cleaning, exploratory data analysis, trend identification, and forecasting for the upcoming year.

**1. Data Cleaning:**
The dataset provided includes sales records of various drink brands across different cities in Greece. However, for this analysis, we focused solely on the Gazoza brand. Data cleaning involved handling missing values, ensuring data consistency, and preparing the dataset for analysis.

**2. Exploratory Data Analysis (EDA):**
EDA was performed to understand the underlying patterns and trends in Gazoza sales over time. We visualized sales trends, examined relationships between variables, and identified potential outliers.

**3. Stationarity Analysis:**
A crucial step in time series analysis is to determine whether the data is stationary or not. Stationarity implies that the statistical properties of the data, such as mean and variance, remain constant over time. We conducted a Dickey-Fuller test to assess stationarity. The test indicated that the data is not stationary; hence, further preprocessing was required.

**4. Preprocessing:**
To achieve stationarity, we performed logarithmic transformation of the sales data. Additionally, we applied differencing to remove trend and seasonality components, resulting in a stationary time series.

**5. Decomposition:**
Decomposition of the time series into its trend, seasonal, and residual components provided insights into the underlying patterns. This facilitated better understanding of the data dynamics and aided in forecasting.

**6. Forecasting:**
We employed the Autoregressive Integrated Moving Average (ARIMA) model for forecasting future sales of Gazoza in Greece. The model was trained on the transformed data and used to predict sales for the upcoming year (2018). Confidence intervals were calculated to assess the uncertainty in the forecasts.

**7. Results:**
The ARIMA model produced forecasts for Gazoza sales in 2018, along with corresponding confidence intervals. The forecasted values were compared against actual test data from 2018 to evaluate the model's performance.

**9. Model Evaluation:**
To ensure the robustness and reliability of the forecasting model, we propose the utilization of nested cross-validation. Nested cross-validation is a powerful technique for model evaluation, particularly in time series analysis, as it addresses issues such as data leakage and overfitting.

**Nested Cross-Validation:**
Nested cross-validation involves two levels of cross-validation loops:
Outer Loop: Divides the dataset into multiple train-test splits. Each split serves as a holdout set for evaluating the model's performance.
Inner Loop: Implements cross-validation within each training set to tune model hyperparameters and select the best configuration.

**Advantages of Nested Cross-Validation:**
Avoids Data Leakage: Nested cross-validation ensures that model evaluation is conducted on unseen data, preventing information leakage from training to testing sets.
Robust Performance Estimation: By averaging performance metrics across multiple iterations, nested cross-validation provides more reliable estimates of model performance.
Hyperparameter Tuning: The inner loop allows for hyperparameter tuning, optimizing model parameters for better generalization.

**Implementation:**
Outer Loop: Split the dataset into multiple train-test splits, ensuring temporal order is maintained. Each split represents a distinct time period.
Inner Loop: Within each training set, perform cross-validation to tune ARIMA model parameters, such as the order of autoregressive (p), integrated (d), and moving average (q) components.
Model Evaluation: Calculate evaluation metrics such as Mean Squared Error (MSE), Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE) for each iteration of the outer loop.
Aggregate Results: Average performance metrics across all outer loop iterations to obtain final model evaluation scores.

**Conclusion:**
By incorporating nested cross-validation into the model evaluation process, we can ensure the robustness and generalizability of the ARIMA forecasting model for demand dataset. This rigorous evaluation approach enhances confidence in the model's predictive capabilities and facilitates informed decision-making for stakeholders in the beverage industry.
