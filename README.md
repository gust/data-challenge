# Data-Challenge

## Overview

Thank you for expressing interest in the Inference Data Scientist position at Gust.
This challenge is designed to test your ability to organize and interpret data.
Please submit your answers by 10 December 2018

## Download Data

- If you would like to use Postgres to access the data, you can use the [PG_DUMP file here](https://s3.amazonaws.com/gust-data-challenge/data_3)
- If you would like the data as a CSV (including headers) it can be [downloaded here](https://s3.amazonaws.com/gust-data-challenge/payments_data.csv)

**For more information on creating postgres database see https://www.postgresql.org/docs/9.1/static/app-createdb.html**

**For more information on using a pg_dump_file see https://www.postgresql.org/docs/9.1/static/backup-dump.html#BACKUP-DUMP-RESTORE**

## Explanation of Dataset

There is only one table named Payments. The table tracks every time someone pays for a service. Every row represents a payment that was made including the time the payment was made, the id of the user that made the payment and the amount that the payment was for

|Column|Description|
|---|---|
|id| ID of row|
|created_at|timestamp of when the payment was made|
|user_id| ID of user that made the payment|
|amount| amount in USD that the payment was for

# Question to answer

We are interested in seeing the Average Revenue Per Customer (ARPC) over time (up to 365 days).
This is used to calculate how much revenue we can expect to get from a customer after a certain amount of time.

In order to calculate the average revenue per customer at a particular day (say day n), we need to calculate 2 things:
  1. How many customers are at least n days old (at least n days between first purchase and today)?
  1. Of those customers above, what was the cumulative total of purchases in their first n days (all purchases made within n days of their first purchase).

Taking answer 2 and dividing by answer 1 gives us the the average revenue per customer at n days
    - Hint: you can use the psql function generate_series to create the numbers between 1 and 365
    
## Example
As an example (not representative of the actual dataset):

Assume we have 10 customers.
- 2 of these customers' oldest purchase is 25 days ago
- 8 of these customers' oldest purchase is 50 days ago
- All 10 customers have an age of at least 25 days

If we want to calculate the ARPC at 25 days, we 
1. take all customers with an age of at least 25 days (10 customers)
2. sum up their purchases that ocurred within their first 25 days as a customer
3. divide by the number of customers with an age of at least 25 days

If we want to calculate the ARPC at 50 days, we 
1. take all customers with an age of at least 50 days (8 customers)
2. sum up their purchases that ocurred within their first 50 days as a customer
3. divide by the number of customers with an age of at least 50 days

Note: Notice how the purchases of the 2 customers with an age of 25 days are not included in the calcuation of ARPC at 50 days.
    
## Expected Output
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
## [CSV Download](https://s3.amazonaws.com/gust-data-challenge/payments_data.csv)
