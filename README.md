# 📊 Employee Attrition Analysis & Predictive Modeling

An end-to-end data science project utilizing Exploratory Data Analysis (EDA) and Machine Learning to uncover systemic drivers of employee turnover and predict flight risks. Built with an HR-centric focus, this project prioritizes model explainability alongside predictive performance to provide actionable intelligence for retention strategies.

---

## 📌 Project Overview
Employee attrition is an expensive challenge for any organization. This project analyzes historical employee data to answer critical workforce questions:
* Which departments and job roles lose the most talent?
* Does salary alone explain attrition, or are work-life balance and burnout stronger factors?
* At what point in an employee's tenure are they most likely to leave?
* Can we build an early-warning system to identify at-risk employees before they resign?

---

## 📂 Dataset Description
The analysis is conducted using the standard HR dataset: **`WA_Fn-UseC_-HR-Employee-Attrition.csv`**. 
It includes features covering:
* **Demographics:** Age, Marital Status, Education, Gender.
* **Role & Compensation:** Department, Job Role, Monthly Income, Stock Options, Job Level.
* **Work Environment:** OverTime status, Work-Life Balance rating, Job Satisfaction, Environment Satisfaction.
* **Tenure:** Years at Company, Years in Current Role, Total Working Years, Years Since Last Promotion.

---

## 📈 Key Business Insights (EDA Summary)
* **The Overtime Trap:** Excessive `OverTime` emerged as the single strongest predictor of employee flight risk. Employees with a **"Bad" (1) Work-Life Balance rating suffer a 31.25% attrition rate**—more than double the company average.
* **Critical Early Tenure:** Attrition is heavily concentrated in an employee’s early career stage, peaking sharply at the **1-year and 2-year marks**.
* **Role-Specific Crises:** The **Sales Representative** role experiences a severe attrition crisis at **39.76%**, making it the highest-risk position in the company.
* **Compensation vs. Burnout:** While leavers earned an average monthly income roughly 30% lower ($4,787) than those who stayed ($6,833), salary alone does not tell the whole story. Burnout from overwork frequently acts as the final push factor.

---

## 🤖 Machine Learning Framework & Evaluation
To handle the inherent class imbalance (more employees stay than leave), models were trained using the `class_weight='balanced'` parameter. We evaluated three algorithms: **Logistic Regression**, **Random Forest**, and **Gradient Boosting**.

### Performance Comparison Table

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression (Best)** | **0.738** | **0.38** | **0.67** | **0.49** | **0.78** |
| Random Forest | 0.857 | 0.64 | 0.30 | 0.41 | 0.81 |
| Gradient Boosting | 0.864 | 0.60 | 0.23 | 0.33 | 0.82 |

### 🏆 Why Logistic Regression Was Chosen
In HR attrition modeling, **Recall is the most critical metric**. Missing an employee who intends to leave (a False Negative) is far more costly than checking in on an employee who is stable (a False Positive). 
* Logistic Regression achieved the highest **Recall (0.67)**, successfully capturing 67% of actual leavers.
* Its linear coefficients provide **direct interpretability**, allowing HR teams to see the exact weights of risk factors rather than relying on a "black box" model.

---

## 📋 Top 10 Drivers of Attrition (Model Feature Importance)
Extracted directly from the Logistic Regression model coefficients, ranked by absolute impact:
1. **OverTime** (High impact: significantly increases exit risk)
2. **MonthlyIncome** (Strong stabilizing anchor: higher income reduces risk)
3. **TotalWorkingYears** (Stabilizing factor)
4. **YearsAtCompany** (Increases risk in early tenure years)
5. **JobLevel** (Stabilizing factor)
6. **MaritalStatus** (Increased risk factor for Single employees)
7. **Age** (Stabilizing factor)
8. **DistanceFromHome** (Increases exit risk)
9. **StockOptionLevel** (Stabilizing factor)
10. **JobSatisfaction** (Stabilizing factor)

---

## 📊 Visualizations Included
The project generates five core visualization assets saved locally as PNGs:
1. **`attrition_by_dept_role.png`**: A grouped bar chart breaking down exit rates across business units.
2. **`income_vs_attrition.png`**: Box plots demonstrating the income spread between staying and leaving cohorts.
3. **`cm_log_reg.png`**: A confusion matrix heatmap illustrating the true vs. false predictions of our best model.
4. **`feature_importance.png`**: A horizontal bar chart ranking the top 10 coefficients driving the model's logic.
5. **`roc_curve_comparison.png`**: A multi-model ROC graph comparing the true positive vs. false positive rates on a shared axis.

---

## 💡 Concrete HR & Business Recommendations
* **Proactive Stay Interviews:** HR should utilize the model's high-risk list to target employees within their first 24 months who are working high overtime hours. Managers should initiate empathetic "stay conversations" before formal resignations occur.
* **Workload Audits & Load Leveling:** Because `OverTime` is the primary catalyst for burnout, the company should mandate workload audits in high-churn divisions (like Sales) and introduce support staff or automation rather than absorbing repeated re-hiring costs.
* **Revamped Onboarding Milestones:** Introduce formal pulse check-ins at the 3, 6, and 12-month marks for new hires to proactively catch alignment issues before they hit the high-risk 1-2 year tenure threshold.

⚠️ **A Note on Model Limitations:** This model flags *statistical correlations*, not definite human *causation*. It cannot capture deeply personal external factors (e.g., family relocations, unrecorded team dynamics, or sudden competitive market offers). It should always be used as an **early-warning support tool** to prompt human-led, supportive outreach—never as a tool for automated employee management.

---
