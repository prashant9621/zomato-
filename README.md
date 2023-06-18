                                                             ZOMATO DATA ANALYSIS

                                                             
CASE STUDY
1-The case study contain of 3 dataset.The analysis is done on the Zomato dataset which includes customer ratings abut 9000+ eatries across all over the world.The other Two data sets are used for data cleaning.
2-this dataset contains answer of question to decide the location,the price range and service for the eatry startup.
![Screenshot (12)](https://github.com/prashant9621/zomato-/assets/136049491/d3f0e5c9-7d3a-46cf-86bc-cfe505988c76)




                                                                 OBJECTIVE

PROBLEM
1-To analyse and determine the ideal cities,Price range,and services for an eatry startup providing North Indian food in Indias central region.

The project consist of 3 data set  > Zomato_dataset
                                    >country_codename
                                   >city_region
                                   


•	which cities have the most number of cateries?
![Screenshot (13)](https://github.com/prashant9621/zomato-/assets/136049491/5497d7d3-1f53-496a-a527-8e94344bfc05)

select city,count(*) as 'no of eateries'
from zomato_dataset
group by city
order by count(*) desc;

Findings
•	In new delhi and noida ,there are more eatries,so there is fierce competition in these cities.
•	Agra,allahabad,varansi,dehradun have fewer eateries.so,there is less competion in these cities.
Solution
•	The eatery startup should concentrate on opening in cities with less competition.

Q-Which low competition cities have the most eateries with aggregated ratings more then 4?
![Screenshot (14)](https://github.com/prashant9621/zomato-/assets/136049491/003b8b0b-30c5-47cb-b9f5-b70206531493)


select city,
sum(case when aggregate >=4.0 then 1 else 0 end ) as 'no_of_eateries'
from zomato_dataset
where city not in ('new delhi ','noida")
group by city
ordr by sum(case when aggregate >=4.0 then 1 else 0 end ) desc;

Findings
•	There are no eatries in allahabad,varansi or ghaziabadwith high aggregate rating 
•	Therefore,new startups may focus upon allahabad,varansi and ghaziabad.


Q-How many eatries have a price range of 1,2,3,4, in allahabad ,varansi,and ghaziabad?

select city,
count(case when price_range =1 then restaurant_id end) as 'price range1',
count(case when price_range =2 then restaurant_id end) as 'price range2',
count(case when price_range =3 then restaurant_id end) as 'price range3',

from zomato_dataset
where city in ('allahabad','varansi','ghaziabad')
group by city;


Findings
•	Allahabad has most of its eatries in price range 3.
•	Varansi has most of its eatries in pricce range 3.
•	Ghaziabad has most of its eatries in price range 1.
•	The price range of new startup should be 3 in these cities.


 Q-How many people have an average cost for two people of less then rs.500,between rs 500 and rs.1000 and more then rs.1000 in allahabad ,varansi,and ghaziabad?

select city,
sum(case when average_cost_for_two <=500 then 1 else 0 end) as "<=",
sum(case when average_cost_for_two between 500 and 1000 then 1 else 0 end) as 'between 500 and 1000',
sum(case when average_cost_for_two >=1000 then 1 else 0 end) as '>=1000'

from zomato_dataset
where city in ('allahabad','varansi','ghaziabad')
group by city;


Findings
•	The eatery startup should have the price of its items between 500 and 1000 in allahabad and varansi.
•	In ghaziabad,it should have the majority of items that are priced less then or equal to 500


Q-How many eatries offer online delivery or table booking service and what are their average consumer votes in allahabad,varansi and ghaziabad?


select city,
round(avg(votes),0) as avg_consumervotes,
sum(case when has_table_booking ="yes" then 1 else 0 end) as table_delivery,
sum(case when has_online_delivery ="yes"then 1 else 0 end) as omline_delivery,
from zomato_dataset
where city in ("allahabad","varansi","ghaziabasd")
group by city;



Findings
•	Average votes is much higher in that restaurant which provide both online and table booking 
•	So,restaurant mainly in allahabad and varansi start online delivery too 

Recomendation
•	To meet the need for high quality eatries,the eatry startup should focus on opening in low competition cities such as allahabad ,varansi, and ghaziabad.
•	The eatry startup should open a budget friendly in ghaziabad .the average cost of two should not exceed rs 1000.
•	The eatry startup should start both table as well as online delivery











