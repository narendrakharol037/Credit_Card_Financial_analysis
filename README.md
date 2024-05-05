# Credit Card Weekly data analysis

## Objective
  To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, 
  enabling stakeholders to monitor and analyze credit card operations effectively.

## Tools Used
### Database - MYSQL
### Visualization Tool - Power bi

## Steps Followed
#### Step 1 - My data is stored in MYSQL database so that firstly i did connect the MYSQL database to Power bi then i did load the data in power bi, in my data two table are present credit_card_transaction table and credit_card_customer table.
#### Step 2 - After that i understand the data and then i performed some opertions on my data like data clensing,data modeling, data transformation.
#### Step 3 - Then i did apply close $ apply after i did save the file by credit_card file name.
#### Step 4 - After i did create two column based on the Age and Income, i did categorize the age and income and create column like Age_group and Income_group.
#### Step 5 - Then i did create some measures based on the dax functions that is given are below.

(a) AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown")

(b) IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown")

(c) week_num2 = WEEKNUM('public cc_detail'[week_start_date])

(d) Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

(e) Current_week_Reveneue = CALCULATE(SUM('public cc_detail'[Revenue]),FILTER(ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

(f) Previous_week_Reveneue = CALCULATE(SUM('public cc_detail'[Revenue]),FILTER(ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

#### Step 6 - After that i created two Pages credit card transaction report and credit card customer report based on the some visuals and KPIS.

### Credit card transaction report

![cc1](https://github.com/narendrakharol037/Credit_Card_Financial_analysis/assets/121941969/45f7d7ce-a712-4623-9083-677d2b458e99)

