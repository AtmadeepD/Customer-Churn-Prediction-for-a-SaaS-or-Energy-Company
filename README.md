# Customer-Churn-Prediction-for-a-SaaS-or-Energy-Company

This end-to-end machine learning project identifies which telecom customers are at risk of churning and connects that risk to potential business impact. Using CatBoost with SMOTE, SHAP for explainability, and a custom risk-scoring framework, we bridge the gap between accurate predictions and actionable business strategy.

---

## 🎯 Project Objective

To accurately predict customer churn and quantify the **financial impact** by:

- Identifying customers most likely to churn
- Understanding why they churn using SHAP values
- Prioritizing intervention based on **value-weighted churn risk**
- Supporting retention strategy with actionable segments

---

## 📦 Dataset

- **Source:** [Kaggle - Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Rows:** 7,032 customers
- **Target Variable:** `Churn` (Yes/No)
- **Features:** Customer demographics, services subscribed, billing, and tenure

---

## 🧭 Workflow Breakdown

### 1. 🧪 Exploratory Data Analysis (EDA)

> Notebook: `1_EDA_Customer_Churn.ipynb`

- Explored churn rate across contract types, internet service, payment methods, tenure, and monthly charges.
- Key findings:
  - **Month-to-month contracts** showed the highest churn rate.
  - Customers with **Fiber optic internet** were more likely to churn.
  - Short tenure and high charges were strong churn indicators.

📌 Visualizations created:
- Churn distribution
- Monthly Charges vs. Tenure
- Churn by Contract Type and Internet Service

---

### 2. 🛠️ Feature Engineering

> Notebook: `2_Feature_Engineering_Churn.ipynb`

- Handled missing values in `TotalCharges`
- Converted categorical variables using one-hot encoding
- Created engineered features to improve prediction:
  - Tenure buckets
  - Revenue per tenure
- Label-encoded the `Churn` column for binary classification

---

### 3. 🤖 Modeling with CatBoost + SMOTE

> Notebook: `3_Modeling_CatBoost_SMOTE.ipynb`

- Model: **CatBoostClassifier** (handles categorical data efficiently)
- Addressed class imbalance using **SMOTE**
- Model Evaluation:
  - Accuracy: ~95%
  - ROC-AUC: ~0.97
  - Balanced performance across precision, recall, and F1

📌 Key outputs:
- Confusion matrix
- ROC curve
- CatBoost feature importance plot

---

### 4. 🔍 Explainability with SHAP

> Notebook: `4_Explainability_SHAP.ipynb`

- Applied **SHAP** to interpret model predictions
- Identified top churn-driving features:
  - Contract type (month-to-month)
  - Tenure (low)
  - Internet service (fiber optic)
  - Online security & tech support
- Used:
  - SHAP summary plots
  - Force plots for local interpretability (individual customers)

📌 Helps translate model outcomes into business language for decision makers

---

### 5. 💼 Business Impact & Risk Segmentation

> Notebook: `5_Business_Impact_Risk_Score.ipynb`

- Used churn probabilities (simulated here) and monthly revenue to compute:
- risk_score = churn_probability * normalized(MonthlyTenureRevenue)
- - Segmented customers by quartiles:
- **Low Risk**
- **Medium Risk**
- **High Risk**
- **Very High Risk**

- Provided per-segment average charges and customer count.

📊 Example Output:
--- Churn Risk Analysis Summary ---

Total Customers: 7032
Low Risk Customers: 4249 (Avg Charges: $51.11)
Medium Risk Customers: 1803 (Avg Charges: $80.39)
High Risk Customers: 827 (Avg Charges: $93.45)
Very High Risk Customers: 152 (Avg Charges: $106.80)

Recommendation: Focus retention strategies on High and Very High Risk segments where customer value is high.


📌 Visualizations:
- *Risk score distribution*

![image](https://github.com/user-attachments/assets/aa290eae-b387-475b-aa0a-c39cc9893471)


- *Customers by risk segment*

![image](https://github.com/user-attachments/assets/43b07d13-782c-4240-9bb7-8bf320b1c0d1)


- *Average charges per risk group*

![image](https://github.com/user-attachments/assets/6d3da7b4-d661-4554-8345-f10e21845bdc)

---

## 📈 Business Value

✅ Highlights customer groups with both **high risk** and **high revenue potential**  
✅ Enables **targeted retention campaigns**  
✅ Improves communication with stakeholders using **interpretable AI outputs**

---

## 🔮 Future Enhancements

- Use model-predicted churn probabilities instead of simulation
- Incorporate **CLV (Customer Lifetime Value)** in risk scoring
- Deploy as an interactive **Streamlit dashboard**
- A/B test retention strategies in real-world business settings

---

## 👨‍💻 Author

**Atmadeep Dey**  
Business Analyst | Energy & AI Strategy | Data Science Portfolio  
[LinkedIn](https://www.linkedin.com/in/atmadeepdey) | [Kaggle](https://www.kaggle.com/atmadeepdey)

---

## 📄 License

This project is open-source and available under the MIT License.

