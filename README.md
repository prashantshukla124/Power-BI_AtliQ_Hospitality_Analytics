# Power-BI_AtliQ_Hospitality_Analytics
# 🏨 AtliQ Grands Hospitality Analytics Project
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/6947e264-0b99-4530-9af2-2b7be58a156d" />

# Live Dashboard Link:

https://app.powerbi.com/view?r=eyJrIjoiMmJjNWEwOGYtMTI1ZS00NDhmLWE2N2ItMjdhYTMwYzE4ODZmIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9

# Business Context
AtliQ Grands is a luxury five-star hotel chain operating across India for over two decades. Despite its legacy and premium positioning in both leisure and business travel segments, the company has recently experienced a decline in market share and revenue. This downturn is largely due to increased competition and several misaligned strategic decisions from top management.

# Project Goal
To build a comprehensive, end-to-end business intelligence solution in Power BI that:

Tracks performance at property, city, and corporate levels in real-time

Identifies revenue-impacting trends and weak spots

Equips executives with data-backed insights to regain market share and increase profitability
# Problem Statement
AtliQ Grands’ senior leadership has acknowledged underperformance and engaged a third-party analytics partner. The objective is to use historical data and business intelligence tools to extract actionable insights, allowing for better strategy, pricing, and operational execution.
# 📊 Data Assets

| Table                     | Grain         | Rows   | Description                                       |
|---------------------------|---------------|--------|---------------------------------------------------|
| `dim_date`                | Daily         | 1,826  | Calendar table (2018–2022)                        |
| `dim_hotels`              | Hotel         | 10     | Hotel attributes (city, brand, star rating)       |
| `dim_rooms`               | Room type     | 7      | Room category, capacity                           |
| `fact_bookings`           | Booking-level | 500K   | Raw bookings including revenue, status, room type |
| `fact_aggregated_bookings`| Day-Hotel     | 180K   | Pre-aggregated KPIs (daily summaries by property) |
# Data Modelling
<img width="1463" height="819" alt="Image" src="https://github.com/user-attachments/assets/467041bb-6966-40b8-af35-6e0df5f38db6" />

📌 **Source**: Public *"Hospitality Challenge"* dataset by **CodeBasics**
# Solution Architecture
# 🔄 Extract & Load
All CSV files loaded using Power BI’s "Get Data from Folder" feature

Queries renamed and structured for clarity and auditability

# ⚙️ Transform (Power Query)
Promoted headers, fixed data types, and removed superfluous columns

Dropped the day_type column from dim_date; recalculated in DAX using business logic (Weekend = Fri & Sat)

# 🧩 Model (Snowflake Schema)
One-to-many relationships defined between fact and dimension tables

fact_bookings as central table; fact_aggregated_bookings for summary metrics

Surrogate keys added where needed
# DAX Calculations
# 🧮 Calculated Columns
DAX
Copy
Edit
week_number = WEEKNUM('dim_date'[date])

day_type = 
VAR wkd = WEEKDAY('dim_date'[date]) 
RETURN IF(wkd IN {6, 7}, "Weekend", "Weekday")
# 📏 Core Measures (26 Total)
Examples:

Revenue = SUM(fact_bookings[revenue_realized])

Total Bookings = COUNT(fact_bookings[booking_id])

Occupancy % = DURN / DSRN

ADR = Revenue / DURN

RevPAR = Revenue / DSRN

Cancellation % = Cancelled Bookings / Total Bookings
# 📏 Key Business Metrics

| Metric                    | Definition                                         |
|---------------------------|----------------------------------------------------|
| **ADR (Average Daily Rate)** | Revenue per sold room                         |
| **RevPAR**                | Revenue per available room                         |
| **Occupancy %**           | Utilized rooms / available rooms                   |
| **Realization %**         | Completed check-outs / reservations                |
| **No-Show Rate %**        | Percentage of bookings where guests didn’t show up |
| **DBRN**                  | Daily Booked Room Nights                           |
| **DSRN**                  | Daily Sellable Room Nights                         |
| **DURN**                  | Daily Utilized Room Nights                         |
| **Cancellation Revenue Loss** | Total value lost due to cancellations         |
# 💡 Dashboard Features

| Feature                    | Description                                                              |
|----------------------------|---------------------------------------------------------------------------|
| 🎯 **Page Navigation**       | Drill-through from corporate → region → hotel                            |
| 📅 **Matrix Calendar Visual**| Shows demand patterns, holiday spikes, and low-demand periods             |
| 📊 **Charts**                | Donut, line, ribbon, combo (line + column), matrix                        |
| 📌 **Clear Filter Bookmark** | One-click reset for all slicers and filters                              |
| 🧠 **Tooltips**              | Provide contextual insights on hover                                      |
| 🎨 **Consistent Dark Theme** | Brand-aligned, low cognitive load, and visual clarity                     |
# Key Insights
# Top Revenue Cities:

Mumbai leads at ₹669M

Followed by Bengaluru, Hyderabad, and Delhi

# Top Property:

AtliQ Exotica: ₹320M in revenue, 57% occupancy, 3.62 average rating

AtliQ Bay: Highest occupancy at 66%

# Week 24:

Peak performance week with ₹139.6M revenue

# Cancellations:

Total loss: ₹298M due to cancellations

Elite rooms: Most booked but also highest cancellation rate

# Delhi:

Highest in both occupancy and customer satisfaction — suggests strong brand equity
## 🛠️ Tools & Skills Demonstrated

### 💻 Technical

- **Power BI**: ETL, DAX, visuals, themes, bookmarks  
- **Data Modelling**: Snowflake schema, relationships, surrogate keys  
- **Power Query**: Data cleaning, transformation  
- **DAX**: Calculated columns & measures  

### 🧠 Domain Knowledge

- **Hospitality KPIs**: ADR, RevPAR, occupancy, no-show rate  
- **Cancellation Policies**: 60–90% fee if cancelled within 3 months  

### 🗣 Soft Skills

- Interpreting stakeholder mock-ups  
- Dashboard storytelling & user experience  
- Aligning visuals with business strategy  
# Lessons Learned
Built a custom calendar heatmap using matrix visual

Bookmarks are powerful for both navigation and resetting filters

Visual clarity improves with a single, brand-aligned color palette

Hospitality industry has complex cancellation dynamics impacting revenue

![Image](https://github.com/user-attachments/assets/e2463137-b8b6-481d-9044-2070c9563327)
![Image](https://github.com/user-attachments/assets/9ed00e1b-4335-4dd7-9589-1dfa7d7a8435)
# Dashboard Snapshot
<img width="983" height="553" alt="Image" src="https://github.com/user-attachments/assets/edff883e-7517-4551-ae9d-238c637f622a" />
<img width="1039" height="553" alt="Image" src="https://github.com/user-attachments/assets/3356cbad-543b-48ec-b416-0c31dc00120c" />
<img width="1085" height="546" alt="Image" src="https://github.com/user-attachments/assets/36d749c7-8e46-4f70-8995-03b8dfd27b80" />
<img width="976" height="556" alt="Image" src="https://github.com/user-attachments/assets/b8a31fa0-c5a4-4398-b4ca-0770d5e1b8b4" />

![Image](https://github.com/user-attachments/assets/a0f3981b-d4fb-407b-8c13-44efbebb3a49)
# Live Dashboard Preview

https://github.com/user-attachments/assets/b2c41b9a-90ea-4ccd-b846-1e916d90efba
# Result
This Power BI dashboard has equipped AtliQ Grands with an intuitive, data-driven tool that simplifies decision-making, enhances booking channel performance, and sharpens operational analysis. Within the first quarter of implementation, the company achieved a 20% boost in operational efficiency and saw a 15% improvement in revenue optimization.
# 🤝 Let's Connect!
If you’re interested in hospitality analytics, Power BI consulting, or similar data projects — feel free to reach out!
