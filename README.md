# Project Background
Database project involving SQL query cleaning, sorting, and organization to communicate insights effectively. Database from a fictional Class 8 trucking company spanning three years. Not scraped web data or simplified tutorial content although an realistic simulation built from 12 years of real-world logistics experience.

# Project Objective
Analyse database and answer the following questions:

-Which drivers have the highest on-time delivery rate?

-Which drivers generate the highest revenue per mile?

-Which drivers have the lowest fuel efficiency?

-What is the incident rate per driver?

-Is there a correlation between safety incidents and late deliveries?

-Which drivers have the highest detention time?

# Executive Summary
# Overview of Findings
```sql
--Which drivers have the highest on-time delivery rate?
SELECT DISTINCT first_name||' '||last_name as Full_Name ,Sum(drivers_Monthly_Metrics.on_time_delivery_rate) as on_time_delivery_rate FROM drivers
INNER JOIN drivers_Monthly_Metrics on drivers.driver_id=drivers_Monthly_Metrics.driver_id
GROUP by Full_name
ORDER BY on_time_delivery_rate DESC;
--Insight:
--Drivers with highest on-time delivery rate indicate that they are following quick routes that make deliveries be on time without worrying about Traffic and other safety incident factors
```
```sql
--Which Drivers generate the highest revenue per mile?
SELECT first_name||' '||last_name as full_name,drivers_Monthly_Metrics.total_miles as total_miles,drivers_Monthly_Metrics.total_revenue as total_revenue
FROM drivers
INNER JOIN drivers_Monthly_Metrics on drivers.driver_id=drivers_Monthly_Metrics.driver_id
GROUP BY full_name
ORDER BY total_miles DESC;
--Insight:
--Drivers who generate highest revenue per mile indicate they have more trips taken and are more profitable for the business
```
```sql
--Which drivers have the lowest fuel efficiency?
SELECT first_name||' '||last_name AS Full_name,fuel_purchases.total_cost FROM drivers
INNER JOIN fuel_purchases on drivers.driver_id=fuel_purchases.driver_id
Group By full_name
ORDER BY total_cost ASC;
--Insight:
--Drivers with lowest fuel efficiency indicate that they use fuel efficiency and use proper routess to preserve fuel 
```
```sql
--What is the incident rate per driver?
SELECT first_name||' '||last_name as full_name,count( safety_incidents.incident_type ) as number_of_incidents FROM drivers
LEFT JOIN safety_incidents on drivers.driver_id=safety_incidents.driver_id
GROUP BY full_name
ORDER BY number_of_incidents DESC;
--Insight:
--The higher the incident rate per driver is indicates the routes the driver takes or circumstances the driver experiences are the business problem
```
```sql
--Is there an correlation between safety_incidents and late deliveries?
SELECT safety_incidents.incident_type,safety_incidents.description,safety_incidents.preventable_flag,on_time_flag FROM delivery_events
INNER JOIN safety_incidents on delivery_events.trip_id=safety_incidents.trip_id
ORDER BY incident_type ASC;
--Insight:
--Correlation between safety incidents and late deliveries shows most affected deliveries are from incidents like natural disasters,package damage and traffic.
```
```sql
--Which drivers have the highest detention time?
SELECT first_name||' '||last_name as full_name,sum(delivery_events.detention_minutes) as total_detention FROM drivers
INNER JOIN fuel_purchases on drivers.driver_id=fuel_purchases.driver_id
INNER JOIN delivery_events on fuel_purchases.trip_id=delivery_events.trip_id
Group By full_name
ORDER BY total_detention DESC;
--Insight:
--Drivers with the highest detention times may indicate inefficient delivery locations or scheduling problems.
```
# Recommendations
-Analyze what factors that make the drivers with highest on time delivery rate to implement more in business operations

-Analyze trips that had the highest revenue per mile to promote trips that involve that much miles for higher revenue

-Analyze drivers with lowest fuel efficiency about reasons to factors like routes and trips taken by drivers to achieve lowest fuel efficiency 

-Analyze drivers with highest safety incident with causes and ways to avoid incidents to promote not to be done by other drivers

-Analyze highest detention time drivers and identify factors leading to high detention time

# Tools Used
-SQL

# What This Project Shows
-SQL data querying and analysis

-Data aggregation and metric calculation

-Identifying patterns in operational data

-Translating data results into business insights
