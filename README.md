### Churn Prediction for High-Value Telecom Customers

📌 Project Overview
This project aims to predict customer churn for high-value telecom customers using data from three consecutive months. The goal is to identify churners and the key factors influencing their decision to leave, allowing the telecom company to take proactive measures.

📊 Business Objective
Predict churn in the last (fourth) month using data from the first three months.
Identify important churn indicators to guide business decisions.
Handle class imbalance since churn cases are typically low (5-10%).
Provide actionable insights to reduce churn.

📁 Dataset Overview
The dataset contains customer-level data for 4 months (June-September).
Each column with _6, _7, _8, and _9 represents data for June, July, August, and September respectively.
Data includes recharges, call details, internet usage, roaming, and customer demographics.

🔄 Data Preparation
1. Filter High-Value Customers
Defined high-value customers as those whose average recharge in June & July is ≥ 70th percentile.
About 30,000 rows retained after filtering.

2. Label Churners
A customer is considered churned (churn = 1) if:
No outgoing calls (total_og_mou_9 == 0)
No incoming calls (total_ic_mou_9 == 0)
No internet usage (vol_2g_mb_9 == 0 & vol_3g_mb_9 == 0)
Dropped all columns related to the churn month (_9 columns) since they won't be available at prediction time.

3. Handling Missing Data
Dropped columns with >50% missing values.
Filled remaining missing values:
Numerical values → Replaced with 0
Categorical values → Filled with 'Unknown'

4. Feature Engineering
Created rolling averages for ARPU (Average Revenue Per User):
rolling_arpu_6_7 = mean(arpu_6, arpu_7)
rolling_arpu_7_8 = mean(arpu_7, arpu_8)
Derived 'days since last recharge' from recharge dates.
Removed non-numeric columns before model training.

📊 Exploratory Data Analysis (EDA)
Visualized feature distributions (e.g., ARPU, call minutes, data usage).
Generated correlation heatmaps to find relationships.
Checked class imbalance: ~5% churners vs. 95% non-churners.

🤖 Model Building
1. Data Splitting
80%-20% train-test split for modeling.
Ensured X_train and X_test had consistent features.

2. Handling Class Imbalance
Used class_weight='balanced' in logistic regression.
Experimented with threshold tuning (0.3 instead of default 0.5).
Applied SMOTE oversampling to generate synthetic churner samples.

3. Logistic Regression Model
Used L2 Regularization (Ridge) to prevent overfitting.
Model trained with max_iter=1000 for convergence.

Evaluated using:
ROC AUC Score (to handle class imbalance)
Precision-Recall F1-score

4. Feature Importance
Extracted top 20 most important features from logistic regression.
Plotted feature importance using horizontal bar charts (to prevent overlapping labels).

📈 Model Evaluation

ROC AUC Score: ~0.85

Precision-Recall F1-score: Improved with threshold tuning & SMOTE.

Confusion Matrix: Showed better recall for churners after handling imbalance.

#### Key Insights & Recommendations

High ARPU Decline is a Strong Indicator of Churn

Customers with a sudden drop in ARPU between months are at higher churn risk.

Offer personalized retention plans to these customers.

Data Usage Drop = Higher Churn Risk 📉

Customers who stop using data (esp. 3G/4G) are more likely to churn.

Provide targeted offers (discounts, data boosters) to encourage retention.

Customers With Long Time Since Last Recharge are Likely to Churn 🔄

Those who haven't recharged in the last 15-30 days are high-risk churners.

Send proactive reminders or exclusive recharge discounts.




