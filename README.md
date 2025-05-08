A Power BI dashboard to understand AtliQ hardware goods sales trend.The final dashboard was effective at displaying the sales trend of AtliQ hardware, allowing users to understand the data and make informed decisions.

## Sales Insights Data Analysis Project


Download `db_dump.sql` file to your local computer and import it 
![Screenshot 2025-05-08 225950](https://github.com/user-attachments/assets/45c14ba5-4617-4197-8d88-ec4784b8e5aa)

### Data Analysis Using SQL
![Screenshot 2025-05-08 225909](https://github.com/user-attachments/assets/f7ad7313-3857-4584-b7ef-1129701c2546)

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


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column
![Screenshot 2025-05-08 225841](https://github.com/user-attachments/assets/5c51e9ca-aee6-45f2-bf1d-31be425fa1f2)

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`


