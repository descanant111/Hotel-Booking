--firstly checked out the values of the table 2018
SELECT * FROM dbo.['2018$']

--checked out values in table 2019
SELECT * FROM dbo.['2019$']

--checked out values in table 2020
SELECT * FROM dbo.['2020$']

--union of all table 
SELECT * FROM dbo.['2018$']
union
SELECT * FROM dbo.['2019$']
union
SELECT * FROM dbo.['2020$']

-- Created a table named hotels
with hotels as(
SELECT * FROM dbo.['2018$']
union
SELECT*FROM dbo.['2019$']
union
SELECT*FROM dbo.['2020$']
)

--created column name revenue to check revenue generated 
SELECT arrival_date_year,hotel,round(sum((stays_in_week_nights+stays_in_weekend_nights)*adr),2) as revenue FROM hotels
group by arrival_date_year,hotel


--checked the values of table market segment
select * from dbo.market_segment$

--left join to merge two table 
select* from hotels
left join dbo.market_segment$
on hotels.market_segment=market_segment$.market_segment

--left join to merge two table
left join dbo.meal_cost$
on meal_cost$.meal=hotels.meal