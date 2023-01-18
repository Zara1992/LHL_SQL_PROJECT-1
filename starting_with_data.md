Question 1: 
Q1. Total Transactions and Transaction revenue

SELECT channelgrouping, SUM (totaltransactionrevenue) AS Total_Transaction_Revenue, SUM (transactions) AS Transaction_Number FROM all_sessions 
WHERE totaltransactionrevenue IS NOT NULL AND transactions > 0 
GROUP BY channelgrouping

"channelgrouping","total_transaction_revenue","transaction_number"
"Direct",4704190000,24
"Organic Search",3163670000,22
"Paid Search",394770000,3
"Referral",6018680000,32


Question 2: 

Q2. Identify the channel from which most visitors bounce on the website. 

SELECT channelgrouping ,  COUNT(bounces) AS bounces FROM analytics 
WHERE bounces > 0
GROUP BY channelgrouping
ORDER BY bounces 

"channelgrouping","bounces"
"Affiliates",812
"Display",3165
"Paid Search",3661
"Referral",15961
"Social",67474
"Direct",70443
"Organic Search",313323



