Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: select country, MAX(totaltransactionrevenue) as highest_transaction_revenue from all_sessions
WHERE totaltransactionrevenue is NOT NULL
GROUP BY country
ORDER BY country



Answer:
"country","highest_transaction_revenue"
"Australia",358000000
"Canada",82160000
"Israel",602000000
"Switzerland",16990000
"United States",1015480000

SQL Queries: SELECT city, country, MAX(totaltransactionrevenue) AS highest_transaction_revenue FROM all_sessions
WHERE totaltransactionrevenue is NOT NULL
GROUP BY city, country
ORDER BY city, country

Answer:
"city","country","highest_transaction_revenue"
"Atlanta","United States",742480000
"Austin","United States",122000000
"Chicago","United States",306000000
"Columbus","United States",21990000
"Houston","United States",38980000
"Los Angeles","United States",363000000
"Mountain View","United States",156000000
"Nashville","United States",157000000
"New York","Canada",67990000
"New York","United States",152000000
"not available in demo dataset","United States",1015480000
"Palo Alto","United States",305000000
"San Bruno","United States",103770000
"San Francisco","United States",301000000
"San Jose","United States",154000000
"Seattle","United States",358000000
"Sunnyvale","United States",649240000
"Sydney","Australia",358000000
"Tel Aviv-Yafo","Israel",602000000
"Toronto","Canada",82160000
"Zurich","Switzerland",16990000


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: Country
SELECT  country, Round(AVG(productquantity),2) AS average_products_ordered from all_sessions
WHERE productquantity is not null
GROUP BY country



Answer:
"country","average_products_ordered"
"Argentina",1.0
"Canada",1.0
"Colombia",1.0
"Finland",1.0
"France",1.0
"India",1.0
"Ireland",1.0
"Mexico",1.0
"Spain",10.0
"United States",4.02


SQL Queries: City
SELECT  city, Round(AVG(productquantity),2) AS average_products_ordered from all_sessions
WHERE productquantity is not null
GROUP BY city


Answer:
"city","average_products_ordered"
"(not set)",1.0
"Ann Arbor",1.0
"Atlanta",4.0
"Bengaluru",1.0
"Chicago",1.0
"Columbus",1.0
"Dallas",1.0
"Detroit",1.0
"Dublin",1.0
"Houston",2.0
"Los Angeles",1.0
"Madrid",10.0
"Mountain View",1.0
"New York",1.17
"not available in demo dataset",6.75
"Palo Alto",1.0
"Salem",8.0
"San Francisco",1.0
"San Jose",1.0
"Seattle",1.0
"Sunnyvale",1.0




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:COUNTRY
SELECT country, v2productcategory, SUM(productquantity) FROM all_sessions
WHERE productquantity is not null
GROUP By country, v2productcategory;


Answer:COUNTY
"country","v2productcategory","sum"
"Argentina","Home/Bags/Backpacks/",1
"Canada","${escCatTitle}",1
"Canada","Home/Apparel/Kid's/Kids-Youth/",1
"Canada","Home/Shop by Brand/YouTube/",1
"Colombia","Home/Apparel/Men's/Men's-T-Shirts/",1
"Finland","${escCatTitle}",1
"France","Headgear",1
"India","Apparel",1
"Ireland","Home/Bags/",1
"Mexico","(not set)",1
"Spain","${escCatTitle}",10
"United States","${escCatTitle}",8
"United States","(not set)",10
"United States","Apparel",1
"United States","Bags",54
"United States","Drinkware",1
"United States","Electronics",2
"United States","Home/Apparel/Headgear/",1
"United States","Home/Apparel/Men's/",2
"United States","Home/Apparel/Men's/Men's-Outerwear/",1
"United States","Home/Apparel/Men's/Men's-T-Shirts/",2
"United States","Home/Apparel/Women's/Women's-Outerwear/",1
"United States","Home/Nest/Nest-USA/",13
"United States","Home/Office/Notebooks & Journals/",65
"United States","Home/Shop by Brand/YouTube/",2
"United States","Lifestyle",1
"United States","Nest-USA",4
"United States","Office",1


SQL QUERIES: CITY
SELECT city, v2productcategory, SUM(productquantity) FROM all_sessions
WHERE productquantity is not null
GROUP By city, v2productcategory;

Answer: CITY
"city","v2productcategory","sum"
"(not set)","${escCatTitle}",1
"Ann Arbor","Home/Apparel/Men's/Men's-T-Shirts/",1
"Atlanta","Bags",4
"Bengaluru","Apparel",1
"Chicago","Lifestyle",1
"Columbus","(not set)",1
"Dallas","Home/Shop by Brand/YouTube/",1
"Detroit","Drinkware",1
"Dublin","Home/Bags/",1
"Houston","${escCatTitle}",2
"Los Angeles","Home/Apparel/Men's/Men's-Outerwear/",1
"Madrid","${escCatTitle}",10
"Mountain View","${escCatTitle}",1
"Mountain View","Apparel",1
"Mountain View","Home/Apparel/Women's/Women's-Outerwear/",1
"Mountain View","Home/Nest/Nest-USA/",3
"Mountain View","Nest-USA",1
"New York","${escCatTitle}",1
"New York","(not set)",1
"New York","Home/Apparel/Men's/",1
"New York","Home/Apparel/Men's/Men's-T-Shirts/",1
"New York","Home/Nest/Nest-USA/",2
"New York","Home/Shop by Brand/YouTube/",1
"not available in demo dataset","${escCatTitle}",5
"not available in demo dataset","(not set)",1
"not available in demo dataset","Bags",50
"not available in demo dataset","Electronics",2
"not available in demo dataset","Headgear",1
"not available in demo dataset","Home/Apparel/Headgear/",1
"not available in demo dataset","Home/Apparel/Kid's/Kids-Youth/",1
"not available in demo dataset","Home/Apparel/Men's/",1
"not available in demo dataset","Home/Apparel/Men's/Men's-T-Shirts/",1
"not available in demo dataset","Home/Bags/Backpacks/",1
"not available in demo dataset","Home/Nest/Nest-USA/",3
"not available in demo dataset","Home/Office/Notebooks & Journals/",65
"not available in demo dataset","Home/Shop by Brand/YouTube/",1
"not available in demo dataset","Nest-USA",1
"not available in demo dataset","Office",1
"Palo Alto","Home/Nest/Nest-USA/",1
"Salem","(not set)",8
"San Francisco","Home/Nest/Nest-USA/",1
"San Francisco","Nest-USA",1
"San Jose","Home/Nest/Nest-USA/",1
"Seattle","Home/Nest/Nest-USA/",1
"Sunnyvale","Home/Nest/Nest-USA/",1
"Sunnyvale","Nest-USA",1






**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







