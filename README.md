# ETL-project

**Carolina, Isabel, and Anne**

For our ETL project, we pulled 4 different data sets. We pulled best-selling book data from https://www.kaggle.com/sootersaalu/amazon-top-50-bestselling-books-2009-2019, adult housing accommodations from https://www.census.gov/data/tables/time-series/demo/families/adults.html, US birth data from https://www.census.gov/data/tables/time-series/demo/fertility/his-cps.html#par_list, and US population data from https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-total.html.

For the best-selling book data, the data was provided in a csv format. There was no need for normalization of the data in the csv format. The file was imported into Pandas (using Jupyter Notebook) and converted into a data frame. From there, we sorted the data by year and re-set the index, used loc function to select for books on the best seller list from 2010 to 2017, and made a copy of the data frame to load.

For the US population data, the data was provided in an xlsx format. The data needed to be normalized prior to importing into Pandas (using Jupyter Notebook). In order to normalize the data we removed merged rows that were used to describe the data set, and removed two columns: B (Census aggregate number – this can be calculated during data analysis) and C (Estimates Base). Once imported into Pandas the following operations were done to transform the data before loading to our database: set index to: Country, County and State, renamed the remaining columns tile to “Year”, used the stack function to pull out a column with the year (which became part of the index and the remaining column contained the resident population values), renamed this column to “Resident Population”, reset the index, filtered data to select resident population data from 2010 to 2017, and made a copy of the data frame to load.

For the historical living arrangements dataset, the data was provided in csv format. The data was cleaned in pandas using ‘.dropna’, ‘.drop’, ‘.iloc’, and ‘.loc’ in order to drop null values, the rows with unnecessary years (we only needed the data for 2010-2017), and descriptive table comments which were unessenatial to the raw data. We also had to reset the column headers.

For the data on yearly births per 1,000 women, the transformation process was similar to the historical living arrangements dataset in that we began by dropping null values using ‘.dropna’, renamed all of the column headers, and finished off by dropping rows containing unnecessary values. 

Since our data was all in CSVs, it made more sense to use SQLAlchemy since we didn't use API's or jsons. We created the database loading_db in PGAdmin4 and then used that database to create the 4 tables using SQLAlchemy in Jupyter Notebook: best_sellers, adult_housing, us_births, and us_population. These tables all have year columns from 2010-2017 and can join across that column.
