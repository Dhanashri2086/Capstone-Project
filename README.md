## Capstone-Project:Telecom Churn
Customer churn is a major issue in the telecom industry. This project aims to predict whether a high-value customer will churn based on their usage patterns over a period of four months. The goal is to use machine learning models to identify key indicators of churn and provide actionable insights for retention strategies.

### Data Overview
The dataset contains telecom customer data over four months (June-September), with key features including:
Recharge Amounts: Total amount recharged per month
Call Usage: Incoming and outgoing call minutes
Data Usage: 2G and 3G internet usage

#### Churn Definition
A customer is considered churned (churn=1) if they have:
Zero incoming and outgoing calls
Zero data usage in the final (9th) month

### Data Preparation Steps
Filtering High-Value Customers: Selecting the top 30% based on recharge amounts.
Tagging Churners: Identifying customers who meet the churn definition.
Removing Churn Phase Data: Excluding all columns related to the 9th month to avoid data leakage.

### Exploratory Data Analysis (EDA)
Churn Distribution: Visualization of churned vs. non-churned customers.
Correlation Heatmap: Identifying relationships between recharge, call usage, and churn likelihood.

### Feature Engineering
New features were created to capture behavioral changes:
Recharge Amount Change: Decline in recharge trends.
Call Volume Change: Drop in outgoing and incoming calls.
Data Usage Change: Reduction in internet consumption.

### Machine Learning Models
Three models were trained to predict churn:
Logistic Regression (Baseline, interpretability)
Random Forest (Better handling of complex data)
XGBoost (Best performing model)

### Model Performance
Model                ROC-AUC Score
Logistic Regression  82%
Random Forest        89%
XGBoost              91%

### Key Findings
Recharge amount drop is the strongest predictor of churn.
Call and data usage reductions indicate customers are about to leave.
XGBoost outperformed other models in predicting churn.

### Business Recommendations
1. Offer targeted discounts to customers showing early signs of churn.
2. Improve network quality in areas with declining data usage.
3. Personalized retention strategies based on customer usage trends.

### How to Run This Project
#### Prerequisites
Python 3.x
Required libraries: pandas, numpy, seaborn, matplotlib, sklearn, xgboost, imblearn

#### Steps
1. Clone the repository:
   git clone https://github.com/your-repo/churn-prediction.git
   cd churn-prediction

2. Install dependencies:
   pip install -r requirements.txt

3. Run the Python script:
   python churn_prediction.py

4. View the results in the generated plots and reports.

### Repository Structure
├── churn_prediction.py    # Main Python script

├── README.md              # Project documentation

├── presentation.pdf       # Summary and findings

└── requirements.txt       # Dependencies

### Next Steps
1. Deploy model as an API for real-time churn prediction.
2. Improve model accuracy using deep learning techniques.
3. Test model in production using real-time customer data.





