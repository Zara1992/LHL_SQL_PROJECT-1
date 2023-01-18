What issues will you address by cleaning the data?

Outliers: 2 records that were impossible to insert into the table. I had to remove them from the source all_session.csv
Irrelevant Data: Columns in tables that were null throughout the total number of records. Removed 4 columns from all_sessions.csv, 1 column from analytics
Handling missing data: One record in the product table had missing values but all remaining records were complete. So I removed that particular record. 
Organizing data: Rounded the ratio column in sales_report to 5 decimal place. 


Queries:
Below, provide the SQL queries you used to clean your data.

Outliers: Identified the record line from Visual Studio Code and removed it directly. 

Irrelevant Data Queries:
(not sure why i wasn't able to run the 4 columns as a single query)
ALTER TABLE all_sessions DROP COLUMN productrefundamount;
ALTER TABLE all_sessions DROP COLUMN itemquantity;
ALTER TABLE all_sessions DROP COLUMN itemrevenue;
ALTER TABLE all_sessions DROP COLUMN searchkeyword;
ALTER TABLE analytics DROP COLUMN userid;

Handling Missing Data:
SELECT * FROM products where sku = 'GGADFBSBKS42347’ (Confirmed that there is only 1 record for this SKU)
DELETE FROM products WHERE sku = 'GGADFBSBKS42347’


Organizing Data:
UPDATE sales_report  SET ratio = ROUND (ratio,5)
