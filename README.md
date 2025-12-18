# TELECOM CHURN ANALYSIS
![telecom image](https://github.com/NjorogeWinnie/Telecom-churn-analysis/blob/main/Telecom%20churn/telecom%20image.jpg)

# PROJECT OVERVIEW
Customer churn, the loss of subscribers to competitors, is a significant challenge for SyriaTel as acquiring a new customer is way more expensive than retaining an existing one. This project utilizes machine learning to proactively identify at-risk customers based on their usage patterns and service interactions.

# OBJECTIVES
- **Primary Objective**: Develop a classification model that maximizes recall to identify the highest number of churners before they leave.
- **Secondary Objective**:
1. Identify key behavioral drivers associated with churn.
2. Evaluate performance tradeoffs between different models (Logistic Regression, Decision Trees, Random Forest).
3. Assess model performance using business-relevant metrics (F1-Score, ROC AUC).

# DATA UNDERSTANDING
The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download)
It contains 3,333 customer records with 21 attributes.
- **Target Variable**: `churn`(14.5% churn rate).
- **Key challenge**: There was significant class imbalance, that was addressed using SMOTE to ensure the model learnt the patterns of the minority class.

# FEATURE ENGINEERING
To improve predictive power, we created several behavioral features:
- `Total Minutes`: Aggregated day, evening, night, and international minutes into a single "Total Minutes" metric. This represents the customer's overall reliance on the network regardless of the time of day.
- `Total Charges`: Combined all departmental charges to identify the total "wallet share" SyriaTel holds. This serves as a proxy for price sensitivity—higher spenders are often the first to churn when they perceive a lack of value. 
- `peak_period`: Identified the specific time of day (Day, Evening, Night, or Intl) where the customer has the highest usage.
- `day_night_ratio`: Captured the balance between peak and off-peak usage.
- `intl_usage_flag`: A binary indicator for high-intensity international users.

# METHODOLOGY
1. **Preprocessing**: Numerical features were normalized using StandardScaler, and categorical features were transformed via OneHotEncoder.
2. **Imbalance Handling**: Applied SMOTE exclusively to the training set to prevent data leakage.
3. **Modeling**: Compared a baseline Logistic Regression against a Decision Tree and a Random Forest Ensemble.
4. **Tuning and Optimization**: Conducted a GridSearchCV on the Random Forest model to optimize for recall and fine-tuned the decision threshold (0.65) to balance business priorities.

# MODEL EVALUATION AND PERFORMANCE
