# ETL-project
**Data Cleanup & Analysis**

Once you have identified your datasets, perform ETL on the data. Make sure to plan and document the following:

- The sources of data that you will extract from.

- The type of transformation needed for this data (cleaning, joining, filtering, aggregating, etc).

- The type of final production database to load the data into (relational or non-relational).

- The final tables or collections that will be used in the production database.

- You will be required to submit a final technical report with the above information and steps required to reproduce your ETL process.

**Project Report**

- At the end of the week, your team will submit a Final Report that describes the following:

- Extract: your original data sources and how the data was formatted (CSV, JSON, pgAdmin 4, etc).

We pulled best-selling book data from https://www.kaggle.com/sootersaalu/amazon-top-50-bestselling-books-2009-2019, adult housing accommodations from https://www.census.gov/data/tables/time-series/demo/families/adults.html, US birth data from https://www.census.gov/data/tables/time-series/demo/fertility/his-cps.html#par_list, and US population data from https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-total.html.


- Transform: what data cleaning or transformation was required.

- Load: the final database, tables/collections, and why this was chosen.

Our data was all in CSVs, which made more sense to use SQLAlchemy since we didn't use API's or jsons. We created the database loading_db in PGAdmin4 and then used that to create 5 tables: best_sellers, adult_housing, us_births, and us_population. These tables all have year columns from 2010-2017 and can join across that column.

- Please upload the report to Github and submit a link to Bootcampspot.
