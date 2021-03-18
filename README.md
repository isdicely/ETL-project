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

Best-selling book data
The data was provided in a csv format. There was no need for normalization of the data in the csv format. The file was imported into Pandas (using Jupyter Notebook) and converted into a data frame. There the following operations were done to transform the data before loading to our database:
•	Sorted the data by year and re-set the index.
•	Used loc function to select for books on the best seller list from 2010 to 2017.
•	Made a copy of the data frame to load.

US population data
The data was provided in an xlsx format. The data needed to be normalized prior to importing into Pandas (using Jupyter Notebook). The following steps were taken:
•	Removed merged rows that were used to describe the data set.
•	Removed two columns:
    o	B (Census aggregate number – this can be calculated during data analysis)
    o	C (Estimates Base)
Once imported into Pandas the following operations were done to transform the data before loading to our database:
•	Set index to: Country, County and State
•	Renamed the remaining columns tile to “Year”
•	Used the stack function to pull out a column with the year.
    o	This column became part of the index and the remaining column contained the resident population values.
•	Renamed this column to “Resident Population”.
•	Reset the index.
•	Filtered data to select resident population data from 2010 to 2017.
•	Made a copy of the data frame to load.


- Load: the final database, tables/collections, and why this was chosen.

Our data was all in CSVs, which made more sense to use SQLAlchemy since we didn't use API's or jsons. We created the database loading_db in PGAdmin4 and then used that to create 5 tables using SQLAlchemy in Jupyter Notebook: best_sellers, adult_housing, us_births, and us_population. These tables all have year columns from 2010-2017 and can join across that column.

- Please upload the report to Github and submit a link to Bootcampspot.
