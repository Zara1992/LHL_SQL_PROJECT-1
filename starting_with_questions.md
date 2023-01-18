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
COUNTRY & CITY
SELECT AL.COUNTRY, AL.CITY, SR. productsku, SR.name, SUM (SR.total_ordered) as Total_Ordered from sales_report as SR
INNER JOIN ALL_SESSIONS AL ON SR.PRODUCTSKU = AL.PRODUCTSKU
GROUP BY SR. productsku, SR.name, AL.COUNTRY,  AL.CITY
ORDER BY Total_Ordered desc
LIMIT 100

"country","city","productsku","name","total_ordered"
"United States","not available in demo dataset","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",6346
"United States","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",4560
"United States","not available in demo dataset","GGOEYDHJ056099","22 oz  Bottle Infuser",3800
"United States","not available in demo dataset","GGOEGOCB017499","Leatherette Journal",3190
"United States","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",3060
"United States","not available in demo dataset","GGOEGFYQ016599","Foam Can and Bottle Cooler",2530
"United States","not available in demo dataset","GGOEADHH073999","Android 17oz Stainless Steel Sport Bottle",2505
"United States","Mountain View","GGOENEBB078899"," Cam Indoor Security Camera - USA",2448
"United States","not available in demo dataset","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",2016
"United States","Mountain View","GGOEGOAQ012899","Ballpoint LED Light Pen",1824
"United Kingdom","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",1785
"United States","not available in demo dataset","GGOEYFKQ020699"," Custom Decals",1770
"United States","not available in demo dataset","GGOENEBB078899"," Cam Indoor Security Camera - USA",1734
"United States","Mountain View","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",1568
"United States","not available in demo dataset","GGOEGODR017799","Recycled Mouse Pad",1482
"Germany","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",1368
"United States","Mountain View","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",1336
"United States","Los Angeles","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",1336
"United States","Mountain View","GGOEGOCB017499","Leatherette Journal",1276
"United States","not available in demo dataset","GGOEGDHQ015399","26 oz Double Wall Insulated Bottle",1261
"United States","Mountain View","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",1222
"United States","not available in demo dataset","GGOEGAAX0104"," Men's 100% Cotton Short Sleeve Hero Tee White",1200
"United States","not available in demo dataset","GGOEGBMJ013399","Sport Bag",1190
"United States","not available in demo dataset","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",1128
"United States","not available in demo dataset","GGOEGFKA022299","Keyboard DOT Sticker",1060
"United States","Palo Alto","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",1002
"Canada","not available in demo dataset","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",1002
"United States","New York","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",1002
"United States","San Francisco","GGOEADHH073999","Android 17oz Stainless Steel Sport Bottle",1002
"Japan","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",912
"United States","not available in demo dataset","GGOEGAAX0037"," Sunglasses",876
"United States","not available in demo dataset","GGOEGBJL013999"," Canvas Tote Natural/Navy",868
"United Kingdom","not available in demo dataset","GGOEYDHJ056099","22 oz  Bottle Infuser",800
"United States","Palo Alto","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",784
"Germany","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",680
"United States","San Francisco","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",672
"United States","Sunnyvale","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",672
"India","not available in demo dataset","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",668
"United Kingdom","London","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",668
"United States","Chicago","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",668
"United States","Salem","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",668
"United States","Mountain View","GGOEADHH073999","Android 17oz Stainless Steel Sport Bottle",668
"United States","not available in demo dataset","GGOEGCBQ016499","SPF-15 Slim & Slender Lip Balm",660
"Italy","not available in demo dataset","GGOEGOCB017499","Leatherette Journal",638
"United States","New York","GGOEGOCB017499","Leatherette Journal",638
"United States","not available in demo dataset","GGOENEBQ079199"," Protect Smoke + CO White Wired Alarm-USA",630
"Canada","not available in demo dataset","GGOEYDHJ056099","22 oz  Bottle Infuser",600
"United States","Mountain View","GGOENEBQ079199"," Protect Smoke + CO White Wired Alarm-USA",588
"United States","Mountain View","GGOEGAAX0037"," Sunglasses",584
"United States","not available in demo dataset","GGOEGHPJ080310"," Blackout Cap",567
"United States","San Francisco","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",564
"United States","New York","GGOENEBQ078999"," Cam Outdoor Security Camera - USA",560
"United States","not available in demo dataset","GGOEGBJC019999","Collapsible Shopping Bag",559
"United States","not available in demo dataset","GGOEGAAX0106"," Men's 100% Cotton Short Sleeve Hero Tee Navy",533
"Czechia","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",510
"United States","not available in demo dataset","GGOEGFKQ020799"," Doodle Decal",510
"United States","Sunnyvale","GGOENEBB078899"," Cam Indoor Security Camera - USA",510
"United States","Mountain View","GGOEGFYQ016599","Foam Can and Bottle Cooler",506
"Brazil","not available in demo dataset","GGOEGFYQ016599","Foam Can and Bottle Cooler",506
"Germany","not available in demo dataset","GGOEGFYQ016599","Foam Can and Bottle Cooler",506
"United States","not available in demo dataset","GGOEYHPB072210"," Twill Cap",504
"United States","not available in demo dataset","GGOEGOFH020299"," Screen Cleaning Cloth",504
"United States","New York","GGOEADHH073999","Android 17oz Stainless Steel Sport Bottle",501
"United States","not available in demo dataset","GGOEAKDH019899","Windup Android",480
"United States","not available in demo dataset","GGOEGKAA019299","Switch Tone Color Crayon Pen",476
"United States","New York","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Mexico","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Seattle","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Switzerland","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","San Jose","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Sunnyvale","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Taiwan","(not set)","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"South Korea","Seoul","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Spain","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Netherlands","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Palo Alto","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Los Angeles","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"India","Pune","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","San Francisco","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Croatia","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Mountain View","GGOENEBQ079099"," Protect Smoke + CO White Battery Alarm-USA",456
"United States","Boston","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"Malaysia","not available in demo dataset","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","Santa Clara","GGOEGOAQ012899","Ballpoint LED Light Pen",456
"United States","not available in demo dataset","GGOEGAAX0318"," Men's Short Sleeve Hero Tee Black",448
"Denmark","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",425
"Canada","not available in demo dataset","GGOEYOCR077799"," Hard Cover Journal",425
"United States","Palo Alto","GGOENEBB078899"," Cam Indoor Security Camera - USA",408
"United States","not available in demo dataset","GGOEGFKQ020399"," Laptop and Cell Phone Stickers",403
"United States","Mountain View","GGOEGHPJ080310"," Blackout Cap",378
"United States","Palo Alto","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",376
"United States","Sunnyvale","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",376
"United States","Chicago","GGOENEBJ079499"," Learning Thermostat 3rd Gen-USA - Stainless Steel",376
"United States","Mountain View","GGOEGFKA022299","Keyboard DOT Sticker",371
"United States","Mountain View","GGOEGCBQ016499","SPF-15 Slim & Slender Lip Balm",360
"United States","not available in demo dataset","GGOENEBQ079099"," Protect Smoke + CO White Battery Alarm-USA",360
"India","not available in demo dataset","GGOEYDHJ056099","22 oz  Bottle Infuser",350
"United States","not available in demo dataset","GGOEGOAB021499","Metal Texture Roller Pen",336
"Ireland","Dublin","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",334
"Singapore","(not set)","GGOEGDHC074099"," 17oz Stainless Steel Sport Bottle",334






**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







