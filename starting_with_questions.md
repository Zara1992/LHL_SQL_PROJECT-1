Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SELECT country,city, MAX (totaltransactionrevenue) AS highest_transaction_revenue FROM all_sessions
WHERE totaltransactionrevenue is NOT NULL
GROUP BY country,city
ORDER BY highest_transaction_revenue DESC

"country","city","highest_transaction_revenue"
"United States","not available in demo dataset",1015480000
"United States","Atlanta",742480000
"United States","Sunnyvale",649240000
"Israel","Tel Aviv-Yafo",602000000
"United States","Los Angeles",363000000
"United States","Seattle",358000000
"Australia","Sydney",358000000
"United States","Chicago",306000000
"United States","Palo Alto",305000000
"United States","San Francisco",301000000
"United States","Nashville",157000000
"United States","Mountain View",156000000
"United States","San Jose",154000000
"United States","New York",152000000
"United States","Austin",122000000
"United States","San Bruno",103770000
"Canada","Toronto",82160000
"Canada","New York",67990000
"United States","Houston",38980000
"United States","Columbus",21990000
"Switzerland","Zurich",16990000


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SELECT  country, city ,Round(AVG(productquantity),2) AS average_products_ordered FROM all_sessions
WHERE productquantity is not null
GROUP BY country, city
ORDER BY average_products_ordered desc

"country","city","average_products_ordered"
"United States","not available in demo dataset",10.58
"Spain","Madrid",10.00
"United States","Salem",8.00
"United States","Atlanta",4.00
"United States","Houston",2.00
"United States","New York",1.17
"Ireland","Dublin",1.00
"Mexico","not available in demo dataset",1.00
"United States","(not set)",1.00
"United States","Ann Arbor",1.00
"United States","Chicago",1.00
"United States","Columbus",1.00
"United States","Dallas",1.00
"United States","Detroit",1.00
"United States","Los Angeles",1.00
"United States","Mountain View",1.00
"United States","Palo Alto",1.00
"United States","San Francisco",1.00
"United States","San Jose",1.00
"United States","Seattle",1.00
"Argentina","not available in demo dataset",1.00
"United States","Sunnyvale",1.00
"Canada","not available in demo dataset",1.00
"Colombia","not available in demo dataset",1.00
"Finland","not available in demo dataset",1.00
"France","not available in demo dataset",1.00
"India","Bengaluru",1.00




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


tep1: Checking records where productquantity exits (Output = 53 records out of 15132)

SELECT country, city v2productcategory, productquantity  
FROM all_sessions
WHERE productquantity is not null

"country","v2productcategory","productquantity"
"United States","Palo Alto",1
"United States","Dallas",1
"Finland","not available in demo dataset",1
"United States","Atlanta",4
"Spain","Madrid",10
"Argentina","not available in demo dataset",1
"United States","New York",1
"United States","Sunnyvale",1
"United States","Sunnyvale",1
"United States","Los Angeles",1
"United States","not available in demo dataset",1
"United States","New York",1
"United States","not available in demo dataset",1
"Canada","not available in demo dataset",1
"United States","Mountain View",1
"United States","New York",1
"Mexico","not available in demo dataset",1
"United States","not available in demo dataset",1
"Ireland","Dublin",1
"United States","not available in demo dataset",65
"United States","Mountain View",1
"United States","(not set)",1
"United States","Ann Arbor",1
"United States","Mountain View",1
"United States","not available in demo dataset",1
"United States","New York",2
"United States","Mountain View",1
"United States","New York",1
"United States","San Francisco",1
"United States","New York",1
"United States","not available in demo dataset",1
"United States","not available in demo dataset",50
"United States","Mountain View",1
"United States","Mountain View",1
"Canada","not available in demo dataset",1
"France","not available in demo dataset",1
"United States","San Francisco",1
"United States","not available in demo dataset",1
"United States","not available in demo dataset",1
"Canada","not available in demo dataset",1
"United States","not available in demo dataset",3
"United States","Chicago",1
"United States","Mountain View",1
"United States","Salem",8
"United States","Seattle",1
"United States","Detroit",1
"United States","not available in demo dataset",1
"India","Bengaluru",1
"United States","not available in demo dataset",1
"United States","San Jose",1
"Colombia","not available in demo dataset",1
"United States","Houston",2
"United States","Columbus",1




Step 2: (Output = 48 records out of 53)
SELECT country, city, v2productcategory, SUM (productquantity) AS product_quantity FROM all_sessions
WHERE productquantity is not null
GROUP By country, city, v2productcategory
ORDER BY product_quantity DESC

"country","city","v2productcategory","product_quantity"
"United States","not available in demo dataset","Home/Office/Notebooks & Journals/",65
"United States","not available in demo dataset","Bags",50
"Spain","Madrid","${escCatTitle}",10
"United States","Salem","(not set)",8
"United States","Atlanta","Bags",4
"United States","not available in demo dataset","Home/Nest/Nest-USA/",3
"United States","not available in demo dataset","${escCatTitle}",3
"United States","Mountain View","Home/Nest/Nest-USA/",3
"United States","Houston","${escCatTitle}",2
"United States","New York","Home/Nest/Nest-USA/",2
"United States","not available in demo dataset","Electronics",2
"United States","Ann Arbor","Home/Apparel/Men's/Men's-T-Shirts/",1
"United States","Chicago","Lifestyle",1
"United States","Columbus","(not set)",1
"United States","Dallas","Home/Shop by Brand/YouTube/",1
"United States","Detroit","Drinkware",1
"United States","Los Angeles","Home/Apparel/Men's/Men's-Outerwear/",1
"United States","Mountain View","${escCatTitle}",1
"United States","Mountain View","Apparel",1
"United States","Mountain View","Home/Apparel/Women's/Women's-Outerwear/",1
"United States","Mountain View","Nest-USA",1
"United States","New York","${escCatTitle}",1
"United States","New York","(not set)",1
"United States","New York","Home/Apparel/Men's/",1
"United States","New York","Home/Apparel/Men's/Men's-T-Shirts/",1
"United States","New York","Home/Shop by Brand/YouTube/",1
"United States","not available in demo dataset","Home/Apparel/Headgear/",1
"United States","not available in demo dataset","Home/Apparel/Men's/",1
"United States","not available in demo dataset","Nest-USA",1
"United States","not available in demo dataset","Office",1
"United States","Palo Alto","Home/Nest/Nest-USA/",1
"United States","San Francisco","Home/Nest/Nest-USA/",1
"United States","San Francisco","Nest-USA",1
"United States","San Jose","Home/Nest/Nest-USA/",1
"United States","Seattle","Home/Nest/Nest-USA/",1
"United States","Sunnyvale","Home/Nest/Nest-USA/",1
"Argentina","not available in demo dataset","Home/Bags/Backpacks/",1
"United States","Sunnyvale","Nest-USA",1
"Canada","not available in demo dataset","${escCatTitle}",1
"Canada","not available in demo dataset","Home/Apparel/Kid's/Kids-Youth/",1
"Canada","not available in demo dataset","Home/Shop by Brand/YouTube/",1
"Colombia","not available in demo dataset","Home/Apparel/Men's/Men's-T-Shirts/",1
"Finland","not available in demo dataset","${escCatTitle}",1
"France","not available in demo dataset","Headgear",1
"India","Bengaluru","Apparel",1
"Ireland","Dublin","Home/Bags/",1
"Mexico","not available in demo dataset","(not set)",1
"United States","(not set)","${escCatTitle}",1







**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







