# Sales Insights Data Analysis Project

### Project Overview
This Data Analysis Project for AtliQ Hardware aims to analyze and visualize sales data to identify key trends, optimize sales strategies, and improve overall business performance. This project involves data cleaning, processing, and creating insightful dashboards to support data-driven decision-making.

### Data Sources
Sales Data: The primary dataset used for this analysis is the "salesinfo.sql" file, containing detailed information about each sale made by the company.

### Tools
SQL Server - Data Analysis
PowerBI - Creating reports

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


### Data Analysis Using Power BI

1. Formula to create norm_amount column

= Table.AddColumn(#"Filtered Rows1", "Actual_sales_amt", each if [currency] = "USD#(cr)" then [sales_amount]*75 else [sales_amount])
