# Sales Insights Data Analysis Project
Atliq Hardware is a company which supplies the hardware peripherals to different clients.The Sales Insights - Bricks and Mortar Business project aimed to enhance the decision-making process for AtliQ Hardware by leveraging data-driven insights. I designed a Power BI Dashboard and utilized SQL to analyze and visualize sales trends, empowering employees to make informed decisions for revenue growth in upcoming quarters. The dashboard offers a comprehensive view of AtliQ Hardware's sales performance, including revenue trends, city-wise sales, top customers, top products, and sales quantities. This project was pivotal in optimizing the business's sales strategy.
1. dataset.sql contains the dataset for my project. 

### Data Analysis Using SQL

1. Show all customer records

    SELECT * FROM customers;

1. Show total number of customers

    SELECT count(*) FROM customers;

1. Show transactions for Chennai market (market code for Mumbai is Mark002

    SELECT * FROM transactions where market_code='Mark002';

1. Show distrinct product codes that were sold in Mumbai

    SELECT distinct product_code FROM transactions where market_code='Mark002';

1. Show transactions where currency is US dollars

    SELECT * from transactions where currency="USD"

1. Show transactions in 2020 join by date table

    SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

1. Show total revenue in year 2020,

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";
	
1. Show total revenue in year 2020, January Month,

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

1. Show total revenue in year 2020 in Mumbai

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark002";


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)


