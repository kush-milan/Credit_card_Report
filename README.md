# Credit Card Report using SQL and Power Bi

## Project Overview

The Credit Card Financial Report Dashboard is a Business Intelligence project built using Power BI, MySQL, SQL, and DAX. It provides a comprehensive analysis of credit card transactions, customer demographics, and revenue performance. The dashboard enables stakeholders to monitor key financial metrics, identify spending trends, and make data-driven business decisions through interactive visualizations


📊 Dashboard Previewhttps

[Dashboard](://github.com/kush-milan/Credit_card_Report/blob/main/Screenshot%20%20of%20tha%20Dahbord.png)


## Objectives
Analyze credit card transaction and customer data.
Monitor key financial KPIs such as Revenue, Transaction Amount, Interest Earned, and Transaction Count.
Compare current week performance with previous week performance.
Identify customer spending patterns based on age, income, education, and occupation.
Evaluate card category performance (Blue, Silver, Gold, Platinum).
Analyze revenue by expenditure type and transaction mode.
Build an interactive dashboard using Power BI with dynamic filters and slicers.


🛠️ Tech Stack
Power BI
MySQL
SQL
Power Query
DAX
Data Modeling
Microsoft Excel

📂 Dataset
The project uses two datasets:

1. credit_card

Contains transaction details such as:

Card Category
Annual Fees
Interest Earned
Total Transaction Amount
Total Transaction Count
Revenue
Week Number
Quarter
Expenditure Type
Chip Usage

2. cust_ad

Contains customer information:

Customer ID
Gender
Age
Age Group
Income
Income Group
Education
Job
Marital Status
State


📊 Dashboard KPIs
💰 Total Revenue
💳 Total Transaction Amount
📈 Total Interest Earned
🔄 Total Transaction Count
📅 Current Week Revenue
📅 Previous Week Revenue
📊 Week-over-Week Revenue Growth (%)
👥 Customer Count
💵 Average Revenue per Customer

🔄 Data Transformation Steps
1. Import Data
Imported credit_card.csv and cust_add.csv into MySQL.
Connected Power BI to the MySQL database.


📌 DAX Measures

# Age Group

AgeGroup = SWITCH 
(TRUE(),
'cust_add'[customer_age] <30,"20=30",
'cust_add'[customer_age] >=30 && 'cust_add'[customer_age] <40,"30-40",
'cust_add'[customer_age] >=40 && 'cust_add'[customer_age] <50,"40-50",
'cust_add'[customer_age] >=50 && 'cust_add'[customer_age] <60,"50-60",
'cust_add'[customer_age] >=60, "60+",
"unknown"
)

# IncomeGroup

IncomeGroup = SWITCH(
    TRUE(),
    'cust_add'[Income]<35000, "Low",
    'cust_add'[Income] >= 35000 &&'cust_add'[Income] <70000, "med",
    'cust_add'[Income] >=70000 , "high",
    "unknown"
    )

#  Week_Num2

    Week_Num2 = WEEKNUM('credit_card'[Week_Start_Date])

# Previous_Week_Revenue

Previous_Week_Revenue = CALCULATE(
    SUM('credit_card'[Revenue]),
    FILTER(
        ALL('credit_card'),
        'credit_card'[Week_Num2] = MAX('credit_card'[Week_Num2])-1))

# Current_Week_Revenue

Current_Week_Revenue = CALCULATE(
    SUM('credit_card'[Revenue]),
    FILTER(
        ALL('credit_card'),
        'credit_card'[Week_Num2] = MAX('credit_card'[Week_Num2])))
        
# Revenue

Revenue =
credit_card[Annual_Fees] +
credit_card[Total_Trans_Amt] +
credit_card[Interest_Earned]




📊 Business Insights


Blue Cards generate the highest revenue among all card categories.
Customers aged 30–50 years contribute the largest share of total revenue.
Business professionals are the highest-value customer segment.
Swipe transactions are the most frequently used payment method.
Bills, Grocery, Fuel, and Entertainment account for the majority of customer spending.
Revenue trends vary across quarters, highlighting seasonal customer behavior.
Week-over-week KPIs help monitor business growth and transaction performance.



