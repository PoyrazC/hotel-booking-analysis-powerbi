# Hotel Booking Data Analysis and Visualization
## Data analysis and visualization of hotel booking data using SQL Server, Power BI, and Excel. A complete end-to-end project demonstrating ETL (Extract, Transform, Load), SQL querying, and dashboard creation.

1. Project Overview

A data analysis project focused on hotel booking trends. Using SQL Server for data storage and querying, combined with Power BI for visual storytelling, this project answers key business questions such as:
- Is hotel revenue growing year over year?
- Should we increase parking lot size based on guest car trends?
- What seasonal trends can be observed in bookings and revenue?

2. Tech Stack
- Database: SQL Server (Microsoft SQL Server Management Studio)
- Data Visualization: Power BI
- Data Source: Excel sheets (Historical bookings: 2018–2020)
- Languages: SQL, DAX (Power BI calculations)
- Tools: Excel, Power BI Desktop

3. Project Pipeline

The project workflow follows these key steps:
- Data Import: Import Excel data into SQL Server.
- Database Creation: Create a relational database with normalized tables.
- Data Transformation: Use SQL queries to clean, unify, and join tables.
- Data Analysis: Write SQL queries to calculate revenue, car trends, and seasonal metrics.
- Visualization: Build an interactive Power BI dashboard to present insights.
- Business Questions: Summarize findings and recommendations.

4. Data Workflow
   
  4.1 Database Setup
  - Create a database named hotel_booking_data and import data from Excel into SQL Server.
  
  4.2 SQL Queries for Analysis Key queries include:
  - Combining multiple years of data using UNION:
   
  SELECT * FROM dbo.table_2018
  UNION ALL
  SELECT * FROM dbo.table_2019
  UNION ALL
  SELECT * FROM dbo.table_2020;
  
-  Calculating revenue:
  
  SELECT arrival_date_year, 
       hotel, 
       SUM(adr * (stays_in_week_nights + stays_in_weekend_nights)) AS revenue
  FROM hotels
  GROUP BY arrival_date_year, hotel;

  4.3 Joins with Additional Tables:
  - Joining market segments and meal costs to enhance analysis:

  SELECT h.*, m.discount, mc.meal_cost
  FROM hotels AS h
  LEFT JOIN market_segment AS m 
  ON h.market_segment = m.segment
  LEFT JOIN meal_cost AS mc 
  ON h.meal = mc.meal;

  5. Power BI Dashboard
  The Power BI dashboard addresses the following questions:

     5.1 Revenue Growth:
     
  - Visual: Line chart showing revenue trends over years.
  
     5.2 Parking Lot Decision:
  
  - Metric: Total required car spaces.
  - Visual: Table and line chart showing car usage percentage.
  
     5.3 Trends:
    
  - Visuals: Sparklines for ADR, total room nights, and discount trends.
  
  5.4 Dashboard Layout:

  - Top Section: KPIs – Total Revenue, Average ADR, Total Nights, Car Spaces.
  - Middle Section: Trends – Revenue growth, car space trends.
  - Bottom Section: Segmentation filters – Hotel type, country, and date slicers.
  
  6. Insights and Recommendations

  6.1 Revenue Growth:
     
  - Revenue increased significantly from 2018 to 2019 but dropped in 2020, likely due to incomplete data or external factors.
  
  6.2 Parking Lot Decision:
  
  - Car usage remains stagnant at ~3%, indicating no immediate need for parking lot expansion.
    
  6.3 Seasonal Trends:
  
  - ADR and booking peaks align with seasonal demands, suggesting focused marketing campaigns during peak seasons.
  
  7. Files in the Repository
  - data/: Folder containing the sample Excel data.
  - SQL/: Folder with .sql files for queries used in analysis.
  - powerbi_dashboard.pbix: The final Power BI dashboard file.
  - README.md: Project documentation (this file).
  
  8. How to Run the Project
     
     8.1 Prerequisites:
  - Install SQL Server Management Studio.
  - Install Power BI Desktop.
  
     8.2 Steps:
  - Import Excel files into SQL Server.
  - Execute the provided SQL scripts to clean and analyze the data.
  - Load the query results into Power BI.
  - Open the Power BI file (powerbi_dashboard.pbix) to view the dashboard.

  9. Future Improvements
  - Integrate more granular data (e.g., regional breakdown).
  - Add predictive analytics using Power BI’s forecasting tools.
  - Automate ETL processes with Python or Power Automate.

  

  
