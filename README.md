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
--Which drivers have the highest on-time delivery rate?
SELECT DISTINCT first_name||' '||last_name as Full_Name ,Sum(drivers_Monthly_Metrics.on_time_delivery_rate) as on_time_delivery_rate FROM drivers
INNER JOIN drivers_Monthly_Metrics on drivers.driver_id=drivers_Monthly_Metrics.driver_id
GROUP by Full_name
ORDER BY on_time_delivery_rate DESC;
--Result of query showing the top 2 employees being Thomas Wilson and Mary Wilson
