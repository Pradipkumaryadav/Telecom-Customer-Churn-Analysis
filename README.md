# 📉 Telecom Customer Churn Analysis

**Python (Pandas) + Power BI | End-to-end data cleaning and dashboard project**

Cleaned a messy telecom customer dataset in Python and built an interactive Power BI dashboard to find out **who is leaving and why**, so the business can target retention efforts.

---

## 📌 Business Problem

Customer churn directly reduces revenue. This project answers:

- What is the overall churn rate?
- Which contract types, subscription plans, payment methods and internet services churn the most?
- Does churn differ by state, age group or tenure?
- Where does the revenue come from?

## 🛠️ Tools & Technologies

| Purpose | Tools |
|---|---|
| Raw data | Microsoft Excel |
| Data cleaning & feature engineering | Python, Pandas, NumPy, Jupyter Notebook |
| Dashboard & KPIs | Power BI Desktop, DAX |

## 📂 Repository Structure

```
Telecom-Customer-Churn-Analysis/
├── data/
│   ├── Churn_Unclean_Project.xlsx      # Raw dataset (542 rows, 18 columns)
│   └── Clean_Churn_Data.csv            # Cleaned dataset (23 columns) used in Power BI
├── notebook/
│   ├── Churn_Dataset_Cleaning.ipynb    # Data cleaning & feature engineering
│   └── Churn_Dataset_Cleaning.pdf      # PDF export of the notebook
├── dashboard/
│   ├── Churn_analysis_dashboard.pbix   # Power BI dashboard
│   └── dashboard_preview.png           # Dashboard screenshot
└── README.md
```

## 📋 Dataset Description

Each row is one telecom customer.

| Group | Columns |
|---|---|
| Customer | `Customer_ID`, `Customer_Name`, `Gender`, `Age`, `State`, `City`, `Senior_Citizen`, `Dependents` |
| Service | `Subscription_Type` (Basic/Standard/Premium), `Contract_Type`, `Internet_Service` (DSL/Cable/Fiber/5G), `Tech_Support` |
| Billing | `Tenure_Months`, `Monthly_Charges`, `Total_Charges`, `Payment_Method` |
| Target | `Churn` (Yes/No) |
| Other | `Last_Interaction_Date` |

## 🧹 Data Cleaning (Python)

1. Loaded the raw Excel file and explored it (`head`, `info`, `describe`, `shape`)
2. Checked missing values and **removed duplicate records**
3. Replaced dirty placeholders (`N/A`, `NULL`, blanks) with proper nulls
4. Trimmed extra spaces and standardized text case (name, state, city, gender, subscription, contract, churn)
5. Fixed data types (numeric `Monthly_Charges`, datetime `Last_Interaction_Date`)
6. Removed invalid records: age outside 18–100 and negative charges
7. Handled missing values:
   - `Tech_Support` → "No", `Payment_Method` → "Unknown"
   - `Monthly_Charges`, `Tenure_Months`, `Age` → column mean
   - `Last_Interaction_Date` → median date
8. Exported the final dataset to `Clean_Churn_Data.csv`

## ⚙️ Feature Engineering

| New Column | Logic |
|---|---|
| `Customer_Value` | `Monthly_Charges × Tenure_Months` |
| `Monthly_Revenue` | Copy of `Monthly_Charges` |
| `Tenure_Group` | Bins: 0–12, 13–24, 25–48, 49–72 months |
| `Senior_Flag` | `Senior` if Age ≥ 60, else `Adult` |
| `Churn_Flag` | Yes → 1, No → 0 |

## 📊 Power BI Dashboard

<img width="752" height="399" alt="image" src="https://github.com/user-attachments/assets/738f7a0e-f0f0-489e-ae98-e8ec295a6c0f" />


**KPI cards:** Total Customers · Churned Customers · Retained Customers · Churn Rate · Total Revenue · Average Monthly Charges · Average Tenure

| KPI | Value |
|---|---|
| Total Customers | 445 |
| Churned Customers | 105 |
| Retained Customers | 340 |
| Churn Rate | 23.60% |
| Total Revenue | 22.16M |
| Avg. Monthly Charges | 1.36K |
| Avg. Tenure | 35.95 months |

**Visuals:** churn by contract type, subscription type, payment method, internet service, senior citizen and state (map) · revenue by state · subscription-type slicer for filtering the whole page.

## 🔍 Key Insights

Churn rate = churned customers ÷ total customers in each group.

- **Overall churn is about 1 in 4 customers (~24%).**
- **Subscription:** Standard (27.8%) and Premium (26.6%) churn much more than Basic (16.3%).
- **Contract:** Two-Year customers churn the most (27.2%), higher than Month-to-Month (21.2%), which is unusual and worth investigating.
- **Internet service:** Cable has the highest churn (29.9%); DSL has the lowest (16.8%).
- **Payment method:** UPI (28.7%) and Debit Card (27.8%) users churn most; Cash users churn least (15.1%).
- **Tenure:** Customers with 13–48 months of tenure churn around 28–29%, while customers with 49+ months churn only 14%.
- **Age:** Seniors and adults churn at the same rate (23.7%), so age is not a churn driver here.

## 💡 Recommendations

- Review pricing and value for **Standard and Premium plans**, since paying customers on these plans leave more often.
- Launch retention offers for customers in the **13–48 month tenure window**, where churn peaks.
- Investigate service quality for **Cable** internet users.
- Encourage **Cash/Net Banking style stable payment habits** or autopay incentives for UPI and Debit Card users.
- Look into why **Two-Year contract** customers leave, for example unmet expectations or lack of renewal offers.

## ▶️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/Telecom-Customer-Churn-Analysis.git
cd Telecom-Customer-Churn-Analysis

# 2. Install requirements
pip install pandas numpy openpyxl jupyter

# 3. Run the cleaning notebook
jupyter notebook notebook/Churn_Dataset_Cleaning.ipynb
```

The notebook reads `Churn_Unclean_Project.xlsx`, so update the file path in the load cell if needed. To explore the dashboard, open `dashboard/Churn_analysis_dashboard.pbix` in **Power BI Desktop** (Windows).

## 🚀 Future Improvements

- Use churn **rate** (not just count) in every dashboard visual
- Add SQL queries for churn analysis
- Build a churn prediction model (Logistic Regression / Random Forest)
- Add customer segmentation and a monthly trend page
- Publish the dashboard to Power BI Service

## 👤 Author

**Pradip Kumar Yadav** – Entry-level Data Analyst (SQL · Python · Power BI · Excel)

- LinkedIn: `<add your link>`
- Email: `<add your email>`
- GitHub: `<add your profile link>`

⭐ If you found this project useful, please give it a star!
