🚖  Uber Trips Analysis – Power BI Project
📌 Project Overview

I built this end-to-end Power BI project to analyze Ola/Uber trip data and generate business insights.
The goal was to track KPIs, identify travel patterns, understand payment preferences, and visualize trip demand over time and location.

This project covers everything from data preparation to dashboard design and publishing on Power BI Service.

🎯 Business Goals

Track KPIs such as Total Trips, Total Fare, Duration, Distance, and Night Trip %
Provide geographic insights (top locations & hotspots)
Analyze time-based patterns (day-wise and hourly)
Break down payment methods used by riders
Deliver an interactive and user-friendly dashboard for decision-making


🛠️ My Approach
🔹 Step 1: Data Loading
Imported two tables into Power BI:
Trip Details (Fact) → trip ID, start/end time, fare, distance, payment type
Location (Dimension) → location details
Standardized payment_type column (Cash, Uber Pay, Google Pay, Amazon Pay)

🔹 Step 2: Data Cleaning (Power Query)
Changed column data types (date, text, numeric)
Removed unnecessary rows
Created Day/Night classification for trips
Replaced inconsistent values

🔹 Step 3: Data Modeling
Built a Date Table with DAX to enable time intelligence
Connected Fact and Dimension tables using relationships

🔹Step 4: DAX Measures & Columns

I wrote multiple DAX measures to calculate KPIs:
Total Trips = COUNT('Trip Details'[Trip ID])
Total Fare 
Total Duration 
Total Distance 

🔹Night Trips %:
Night Trip % =
VAR Nightcount = CALCULATE([Total Trips], 'Trip Details'[Shift] = "Night")
RETURN DIVIDE(Nightcount, [Total Trips], 0)

🔹Calculated Column for Shift (Day/Night):
Shift =
VAR _hr = HOUR('Trip Details'[Pickup Time])
RETURN
SWITCH(
    TRUE(),
    _hr>=6 && _hr<=21, "Day",
    _hr>21 && _hr<=23, "Night",
    _hr>=0 && _hr<6, "Night",
    BLANK()
)

🔹Step 5: Dashboard Design

Added KPI cards for Trips, Fare, Duration, Distance, Night %
Used Bar Charts (Trips by Location)
Used Line Charts (Trips by Day & Pickup Time)
Used Donut Charts (Payment Type & Day/Night share)
Created a Filters Panel (Month, Day, Location slicers)
Focused on clean layout & interactivity

🔹 Step 6: Publishing
Published the report to Power BI Service for accessibility


📊 Final Dashboard Preview

📌 Key Insights I Found
🚖 117K total trips generated $1.8M+ in revenue
⏱️ Trips took 1.9M minutes in total covering 394K distance
🌙 Only 8.7% trips were night rides (mostly in urban zones)
💳 Uber Pay + Google Pay = 99% of payments (cash almost negligible)


🧑‍💻 Skills Demonstrated
Power BI Desktop → Data Modeling, Report Design
Power Query → Cleaning & Transformation
DAX → KPIs, Calculated Columns & Measures
Power BI Service → Report Publishing & Sharing
