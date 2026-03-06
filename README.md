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
-Are newer drivers less efficient than experienced drivers?

# Executive Summary
# Overview of Findings
```sql
--Which drivers have the highest on-time delivery rate?
SELECT DISTINCT first_name||' '||last_name as Full_Name ,Sum(drivers_Monthly_Metrics.on_time_delivery_rate) as on_time_delivery_rate FROM drivers
INNER JOIN drivers_Monthly_Metrics on drivers.driver_id=drivers_Monthly_Metrics.driver_id
GROUP by Full_name
ORDER BY on_time_delivery_rate DESC;
--Top 2 drivers with highest on-time delivery rate being Thomas Wilson and Mary Wilson
```
```sql
--Which Drivers generate the highest revenue per mile?
SELECT first_name||' '||last_name as full_name,drivers_Monthly_Metrics.total_miles as total_miles,drivers_Monthly_Metrics.total_revenue as total_revenue
FROM drivers
INNER JOIN drivers_Monthly_Metrics on drivers.driver_id=drivers_Monthly_Metrics.driver_id
GROUP BY full_name
ORDER BY total_miles DESC;
--Top 2 drivers who generate the highest revenue per mile being Charles Hernandez and Linda Davis
```
```sql
--Which drivers have the lowest fuel efficiency?
SELECT first_name||' '||last_name AS Full_name,fuel_purchases.total_cost FROM drivers
INNER JOIN fuel_purchases on drivers.driver_id=fuel_purchases.driver_id
Group By full_name
ORDER BY total_cost ASC;
--Top 2 drivers with the lowest fuel efficiency being Robert Taylor and Thomas Martinez
```
