# ELT Project Involving Postgres, SsnowFlake, DBT and lots of trouble
### CSV
The csv file contains craigslist car sales data, that has been previously scrapped.

#### CSV to Postgres.
For this part, the python script shares [here](https://github.com/M254-bto/Lux-ELT/blob/main/csv_to_postgre.py) worked fine
It comprises of a posgres connector and cursor, that were utilized in creating the table, reading the data into the database and dealing with issues that came up involving Data types and missing values


![Screenshot from 2023-11-21 00-56-01](https://github.com/M254-bto/Lux-ELT/assets/60424574/149cd745-8dd7-48e0-9fba-4f62d688a4a4)



![Screenshot from 2023-11-21 00-57-55](https://github.com/M254-bto/Lux-ELT/assets/60424574/8fe5a536-4f9f-493d-b215-c32c564aff4e)

This part creates the table, reads the data from the csv file and feeds it to the database. Also, when comas are part of your data, the database gets confused, because it trates any comma as a seperator

### Postgres to Snowflake
This part was challenging, because of what I came to find out later were security issues with my local postgres database. I tried SQLpipe with their CLI tool.



![SQLpipe template](https://github.com/M254-bto/Lux-ELT/assets/60424574/b3897a23-fcbc-42bf-8ec7-7af1b24f831c)



This is just a template, but it didn't work for me.


I created an account on Estuary so that I can try to automate the stream, but the same issued continued. I tried Airbyte, this was when I realised all these data streaming methods were not being able to access my local database, so I created one on supabase, and used the same migration script, but a different connector. Since supabase is a cloud databasee service, It was easier for Airbyte to access the data and stream it to Snowflake.



![Data in Snowflake warehouse](https://github.com/M254-bto/Lux-ELT/assets/60424574/2faf226f-5764-42e3-8df6-51bc1b55a5cc)


As the data is now loaded in the warehouse it can be transformed then analysed.






