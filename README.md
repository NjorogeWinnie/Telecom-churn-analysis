# TELECOM CHURN ANALYSIS
![telecom image](https://github.com/NjorogeWinnie/Telecom-churn-analysis/blob/main/Telecom%20churn/telecom%20image.jpg)

# Project Overview
Customer churn, the loss of subscribers to competitors, is a significant challenge for SyriaTel, as acquiring a new customer is way more expensive than retaining an existing one. This project utilizes machine learning to proactively identify at-risk customers based on their usage patterns and service interactions.

# Objectives
- **Primary Objective**: Develop a classification model that maximizes recall to identify the highest number of churners before they leave.
- **Secondary Objective**:
1. Identify key behavioral drivers associated with churn.
2. Evaluate performance tradeoffs between different models (Logistic Regression, Decision Trees, Random Forest).
3. Assess model performance using business-relevant metrics (F1-Score, ROC AUC).

# Data Understanding
The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download)
It contains 3,333 customer records with 21 attributes.
- **Target Variable**: `churn`(14.5% churn rate).
- **Key challenge**: There was significant class imbalance that was addressed using SMOTE to ensure the model learnt the patterns of the minority class.

# Feature Engineering
To improve predictive power, we created several behavioral features:
- `Total Minutes`: Aggregated day, evening, night, and international minutes into a single "Total Minutes" metric. This represents the customer's overall reliance on the network regardless of the time of day.
- `Total Charges`: Combined all departmental charges to identify the total "wallet share" SyriaTel holds. This serves as a proxy for price sensitivity—higher spenders are often the first to churn when they perceive a lack of value. 
- `peak_period`: Identified the specific time of day (Day, Evening, Night, or Intl) where the customer has the highest usage.
- `day_night_ratio`: Captured the balance between peak and off-peak usage.
- `intl_usage_flag`: A binary indicator for high-intensity international users.

# Methodology
1. **Preprocessing**: Numerical features were normalized using StandardScaler, and categorical features were transformed via OneHotEncoder.
2. **Imbalance Handling**: Applied SMOTE exclusively to the training set to prevent data leakage.
3. **Modeling**: Compared a baseline Logistic Regression against a Decision Tree and a Random Forest Ensemble.
4. **Tuning and Optimization**: Conducted a GridSearchCV on the Random Forest model to optimize for recall and fine-tuned the decision threshold (0.65) to balance business priorities.

# Model Evaluation And Performance
For SyriaTel, a False Negative (missing a churner) is more costly than a False Positive (giving a discount to a loyal customer). Therefore, we prioritized Recall and F1-Score.
![Model Table](https://github.com/NjorogeWinnie/Telecom-churn-analysis/blob/main/Telecom%20churn/Model%20Table.png)
**The Performance Tradeoff**
While the Decision Tree offered the highest raw recall, the Tuned Random Forest was selected as the final model for deployment. By adjusting the threshold to 0.65, we achieved a superior balance (F1-Score of 0.74), ensuring that our retention efforts are both highly targeted (Precision: 0.83) and broad enough to catch a significant portion of at-risk users.

# Key Drivers Of Churn
Feature importance analysis identified the "Red Flags" SyriaTel should monitor:
![Feature Importance](https://github.com/NjorogeWinnie/Telecom-churn-analysis/blob/main/Telecom%20churn/Feature%20importance.png)
1. **Total Charges**: The strongest predictor; high spenders are the most churn-prone.
2. **Customer Service Calls**: Risk skyrockets after the 3rd call, signaling a "frustration threshold."
3. **International Plan**: Subscribers to this plan churn at a disproportionately higher rate.
4. **Total Minutes**: Overall usage intensity correlates with likelihood of switching.

# Recommendations
- **Proactive Retention**: Flag any customer reaching their 3rd service call for immediate VIP support or supervisor follow-up.
- **High-Value Loyalty**: Target the "Total Charge" leaders with "Thank You" loyalty bonuses before they reach out to competitors.
- **Plan Audit**: Investigate why the International Plan is driving churn—is it the pricing or the connection quality?

# Conclusion
This project successfully demonstrates that machine learning can provide SyriaTel with a significant competitive advantage in customer retention. By shifting from a reactive stance to a predictive, data-driven strategy, the business can now intervene before revenue is lost.

# Contact Details 
For additional details, questions, or collaboration inquiries, please contact: [muthoniwinnie573@gmail](:https://mail.google.com)
