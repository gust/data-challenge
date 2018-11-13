# Data-Challenge

## Overview

Thank you for expressing interest in the Inference Data Scientist position at Gust.
This challenge is designed to test your ability to organize and interpret data.
Please submit your answers by 30 November 2018

## Setting up

- You will need Postgresql 9.1 or higher to access the data, you can download postgres by following the instructions [here](https://www.postgresql.org/download/)
- Once you have postgres installed you can download the dataset we created for the challenge. Click this [link](https://s3.amazonaws.com/gust-data-challenge/data_3) and the data `data_3` file should download
- Using your terminal, create a new database called gust_challenge using the `createdb` command ` createdb gust_challenge` or `createdb.exe -U postgres gust_challenge` for windows(depending on your setup you may need to specify the database host, port and user to run the command)
- Load the data located in the downloaded pg data dump file `data_3` into the newly created database by running ` psql -d gust_challenge < data_3` or `psql.exe -U postgres -d gust_challenge` (once again, you may need to specify the database host, port and user to run the command)
- You can access the database by running the `psql -d gust_challenge` command or `psql -U postgres -d gust_challenge` (possibly with the host, port and user specified)

**For more information on creating postgres database see https://www.postgresql.org/docs/9.1/static/app-createdb.html**

**For more information on using a pg_dump_file see https://www.postgresql.org/docs/9.1/static/backup-dump.html#BACKUP-DUMP-RESTORE**

**For more information on creating a user see https://www.postgresql.org/docs/9.1/static/app-createuser.html**

## Explanation of Data

There is only one table named Payments. The table tracks every time someone pays for a service. Every row represents a payment that was made including the time the payment was made, the id of the user that made the payment and the amount that the payment was for

|Column|Description|
|---|---|
|id| ID of row|
|created_at|timestamp of when the payment was made|
|user_id| ID of user that made the payment|
|amount| amount in USD that the payment was for

# Question to answer

We are interested in seeing the average revenue per customer over time (up to 365 days).
This is used to calculate how much revenue we can expect to get from a customer after a certain amount of time.

In order to calculate the average revenue per customer at a particular day (say day n), we need to calculate 2 things:
  1. How many customers are at least n days old (at least n days between first purchase and today)?
  1. Of those customers above, what was the cumulative total of purchases in their first n days (all purchases made within n days of their first purchase).

Taking answer 2 and dividing by answer 1 gives us the the average revenue per customer at n days
    - Hint: you can use the psql function generate_series to create the numbers between 1 and 365
    
As An example: 
If we have 10 customers who are more than 25 days old (25+ days between their first purchase and today) and 8 of those customers are more than 50 days old, we can calculate the average revenue per customer at 25 days by summing up all the payments made by the 10 customers in their first 25 days and dividing it by 10. For Average revenue per customer at 50 days we sum up all the purchases made by the 8 customers in their first 50 days and divide by 8.
    
The output should be in the form:

|Day|Average revenue per customer|
|---|---|
|0|$x|
|1|$y|
|...|...|
|365| $z|

Where $x represents the calculation above at day 0, $y represents the calculation at day 1, $z represents it at day 365 etc
## Please use this [google form](https://docs.google.com/forms/d/e/1FAIpQLSdJTfdy_hO8V2F6X0phOXijgV27HzRUvEFV1-JqeC3RtiE5YA/viewform) to submit the code used to generate the table above (please be sure to include the same email you used on your application).

If you use any technologies other than postgresql to compute this data, please include the program used as well as any additional modules required in order to run the code.


## [DDL and data file download](https://s3.amazonaws.com/gust-data-challenge/data_3)
