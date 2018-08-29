# Data-Challenge

## Overview

Thank you for expressing interest in the Inference Data Scientist position at Gust.
This challenge is designed to test your familiarity with SQL (of the postgres flavor). When answering these questions please provide the Query used to reach the answer as well as the answer itself.

## Setting up

- You will need Postgresql 9.1 or higher to access the data, you can download postgres by following the instructions [here](https://www.postgresql.org/download/)
- Once you have postgres installed you can download the dataset we created for the challenge. Click this [link](https://s3.amazonaws.com/gust-data-challenge/pg_dump_file) and the data `pg_dump_file` file should download
- Using your terminal, create a new database called gust_challenge using the `createdb` command ` createdb gust_challenge` (depending on your setup you may need to specify the database host, port and user to run the command)
- Load the data located in the downloaded `pg_dump_file` into the newly created database by running ` psql -d gust_challenge < pg_dump_file` (once again, you may need to specify the database host, port and user to run the command)
- You can access the database by running the `psql` command (possibly with the host, port and user specified)

**For more information on creating postgres database see https://www.postgresql.org/docs/9.1/static/app-createdb.html**

**For more information on using a pg_dump_file see https://www.postgresql.org/docs/9.1/static/backup-dump.html#BACKUP-DUMP-RESTORE**

**For more information on creating a user see https://www.postgresql.org/docs/9.1/static/app-createuser.html**

## Explanation of Data

Descriptions of the 4 tables and their columns are as follows:

__startups__: Represents a startup that is able (but not required) to apply for funding

|Column|Description|
|------|-----------|
|id |The identifier for the startup|
|name |The name of the startup|

__investor_groups__: Represents an investor group that is able to receive funding applications

|Column|Description|
|------|-----------|
|id |The identifier for the investor group|
|name |The name of the investor group|


__deals__: Represents a funding application between a startup and an investor group

|Column|Description|
|------|-----------|
|id |The identifier for the deal|
|startup_id |The id of the startup that submitted the funding application|
|investor_group_id |The id of the investor group that the startup submitted the funding application to|


__locations__: A polymorphic table representing the address of startups and investor groups

|Column|Description|
|------|-----------|
|id |The identifier for the location|
|locatable_id |The id of the startup or investor group that the address refers to|
|locatable_type|specifies whether the `locatable_id` references a startup or investor group|
|street_num|The street number of the address|
|street_name|The street name of the address|
|country|The country where the address is located|



# Questions to answer

1. How many startups submitted an application
1. Which startups didn’t submit any applications (name only)
1. Which startup submitted the most applications, and what are the names of the groups they applied to (name of startup and name of investor groups)
1. How many startups applied to a group in a different country than their own

## Please use this [google form](https://docs.google.com/forms/d/e/1FAIpQLSdyv7_iXOh8hXgO6iqsO8qACPuSg1wSqOpRffeD9yFXTA3I4A/viewform) to submit your answers (please be sure to include the same email you used on your application)
