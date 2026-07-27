# Credit Card Report using SQL and Power Bi

## Project Overview

The Credit Card Financial Report Dashboard is a Business Intelligence project built using Power BI, MySQL, SQL, and DAX. It provides a comprehensive analysis of credit card transactions, customer demographics, and revenue performance. The dashboard enables stakeholders to monitor key financial metrics, identify spending trends, and make data-driven business decisions through interactive visualizations

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
2. cust_add

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





