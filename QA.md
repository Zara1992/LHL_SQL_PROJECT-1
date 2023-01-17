What are your risk areas? Identify and describe them.

1. Irrelevant Data: Columns that are all 'NULL' and contain no information to add business value
2. Data in one table should match or correspond to data in another table where the column names are same. However, based on this data I think it's not 100% guranteed that the information across tables matches. 
3. Missing Data: Alot of columns have data for few rows out of the thousands of rows. This makes me question the relevance of the data and how it was captured. 
4. Data Outliers: Outliers are unusual values in your dataset. Found 2 records in the all_session.csv that I believed to be outliers as they were giving me error in loading the data into the table. There was no other way than to remove those records and proceed. 


QA Process:
Describe your QA process and include the SQL queries used to execute it.

My QA process begins once I was able to load the data into the tables. As I did not know the relevance of the data, I thought it's best to keep all the columns/records in the database. 

