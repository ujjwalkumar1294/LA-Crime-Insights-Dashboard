# LA-Crime-Insights-Dashboard
LA Crime Insights Dashboard: Analyze 2020 Los Angeles crime data with an interactive Excel dashboard featuring slicers, charts, and hyperlinks to uncover crime patterns, victim demographics, and spatial-temporal trends using pivot tables and formulas
Overview
The LA Crime Insights Dashboard is an Excel-based project that analyzes crime data from Los Angeles in 2020. It features an interactive dashboard with slicers, charts, and hyperlinks, providing insights into crime patterns, victim demographics, and spatial-temporal trends. Built using Excel's powerful features like pivot tables, formulas, and VBA (optional), this project aims to deliver a user-friendly tool for exploring crime statistics.

Dataset
Scope: Crime incidents in Los Angeles reported in 2020.
Key Columns:
DR_NO: Incident ID
DATE OCC: Date of occurrence
AREA NAME: Geographic area (e.g., Southwest, Hollywood)
Crm Cd Desc: Crime description (e.g., Robbery, Battery)
Vict Age, Vict Sex, Vict Descent: Victim demographics
Weapon Desc: Weapon used
Premis Desc: Location of crime
LAT, LON: Geographic coordinates
Features
Data Cleaning:
Standardized dates (DATE OCC) and times ('TIME OCC').
Handled missing values: Vict Age (0 or blank) replaced with "N/A".
Analyses:
Crime frequency by area, crime type, and time (day/hour).
Victim demographics (age groups, sex).
Premises and weapons used in crimes.
Interactive Dashboard:
Slicers for filtering by AREA NAME, Crm Cd Desc, Vict Sex, and Date Occurred.
Charts: Bar (area-wise crimes), Pie (crime types), Histogram (victim age), Line (hourly trends).
Navigation:
Hyperlinks via a Table of Contents (TOC) sheet to jump between raw data, cleaned data, analysis, and dashboard.
Optional VBA: Macro to refresh all pivot tables with a button click.
Progress Log
Day 1 (2025-04-02): Initialized repository, imported raw crime data into Excel as 'Raw Data' sheet.

Day 2 (2025-04-03): Cleaned the dataset in a new Cleaned Data sheet to prepare it for analysis. Steps included:

Copied all data from Raw Data to Cleaned Data for processing.
Standardized DATE OCC (column C) into a Date Occurred column using =DATEVALUE(LEFT(C2,10)) to extract the date (e.g., "2020-01-01") from the full timestamp (e.g., "2020-01-01 12:30:00"), formatted as MM/DD/YYYY.
Converted TIME OCC (column D) from numeric format (e.g., 1340 for 1:40 PM) to a Time Occurred column with =TIME(INT(D2/100),MOD(D2,100),0), formatted as HH:MM AM/PM for time-based analysis.
Handled missing values:
Vict Age (column L): Added Cleaned Vict Age (column M) with =IF(OR(L2=0,L2=""),"N/A",L2) to replace 0 or blank entries with "N/A", preserving valid ages (e.g., 23, 55).
Vict Sex (column M): Added Cleaned Vict Sex (column N) with =IF(M2="X","Unknown",M2) to replace "X" (unknown) with "Unknown", keeping "M" or "F" as-is.
Vict Descent (column N): Added Cleaned Vict Descent (column O) with =IF(N2="X","Unknown",N2) to mark "X" as "Unknown", retaining valid descent codes (e.g., "H", "W").
Formatted the cleaned dataset as an Excel table named CrimeData (Ctrl+T) to enable dynamic referencing for pivot tables and slicers.
Verified data integrity by filtering for "N/A" and "Unknown" values to ensure proper handling of missing entries.
Day 3 (2025-04-04): Enhanced Analysis sheet in la_crime_insights_dashboard.xlsx with 6 pivot tables and charts for valuable dashboard insights. Steps included:

Added pivot tables:
Crime by Area: Rows = AREA NAME, Values = Count of DR_NO (A3).
Top 5 Crime Types: Rows = Crm Cd Desc, Values = Count of DR_NO, filtered top 5 (G3).
Victim Age: Rows = Age Group (helper column: =IF(M2="N/A","Unknown",IF(M2<=18,"0-18",IF(M2<=30,"19-30",IF(M2<=50,"31-50","51+"))))), Values = Count of DR_NO (M3).
Crime by Hour: Rows = Hour (=HOUR([@[Time Occurred]])), Values = Count of DR_NO (S3).
Crime by Sex and Age: Rows = Age Group, Columns = Cleaned Vict Sex, Values = Count of DR_NO (Y3).
Top 5 Weapons: Rows = Weapon Desc, Values = Count of DR_NO, filtered top 5 (AE3).
Created charts:
Bar: “Crime Distribution by Area” (A25).
Pie: “Top 5 Crime Types” (G25).
Histogram: “Victim Age Distribution” (M25, Gap Width = 0%).
Line: “Crime Trends by Hour of Day” (S25).
Stacked Bar: “Crime by Victim Sex and Age Group” (Y25).
Column: “Top 5 Weapons Used in Crimes” (AE25).
Positioned charts below pivot tables for clarity.
Updated the Excel file in the repository with these analyses.
Day 4 (2025-04-05): Created an interactive Dashboard sheet in la_crime_insights_dashboard.xlsx to visualize crime insights. Steps included:

Added a new Dashboard sheet and copied 6 charts from Analysis:
Bar: “Crime Distribution by Area” (B2).
Pie: “Top 5 Crime Types” (H2).
Histogram: “Victim Age Distribution” (B20) using Age Group.
Line: “Crime Trends by Hour of Day” (H20).
Stacked Bar: “Crime by Victim Sex and Age Group” (B38).
Column: “Top 5 Weapons Used in Crimes” (H38).
Added slicers for interactivity:
Inserted slicers for AREA NAME, Crm Cd Desc, Cleaned Vict Sex, Date Occurred, Weapon Desc, and Hour (positioned at N2:N40).
Connected slicers to all 6 pivot tables on Analysis (A3, G3, M3, S3, Y3, AE3) for dynamic filtering.
Added Weapon Desc to analyze crime severity and weapon usage, enhancing the "Top 5 Weapons" chart; added Hour for granular time analysis, amplifying the "Crime Trends by Hour" chart.
Included key metrics at the top:
Total Crimes (C1): =COUNT('Cleaned Data'!A:A) for incident count.
Most Common Crime (E1): =INDEX('Cleaned Data'!D:D,MATCH(MAX(COUNTIF('Cleaned Data'!D:D,'Cleaned Data'!D:D)),COUNTIF('Cleaned Data'!D:D,'Cleaned Data'!D:D),0)) to identify the top crime type.
Polished the layout:
Added title “LA Crime Insights Dashboard” (A1, merged A1:G1, bold 16pt).
Arranged charts in a 2x3 grid with slicers on the right and metrics above.
Applied a consistent theme for visual appeal.
Updated the Excel file in the repository with the enhanced dashboard.
Day 5 Progress: Dashboard Development
Pivot Tables and Charts Created:

Crime by Area: Rows = AREA NAME, Values = Count of DR_NO (Bar Chart).
Crime by Time (Hours): Rows = Hour, Values = Count of DR_NO (Line Chart).
Crime by Weapon: Rows = Weapon Desc, Values = Count of DR_NO (Bar Chart).
Crime by Description: Rows = Crm Cd Desc, Values = Count of DR_NO (Pie Chart).
Case Status by Area: Rows = AREA NAME, Columns = Status Desc, Values = Count of DR_NO (Stacked Bar Chart).
Crime by Age Group: Rows = Age Group (0-15, 16-30, 31-45, 46-60, 60+), Values = Count of DR_NO (Histogram).
Crime by Age Group & Sex: Rows = Age Group, Columns = Vict Sex, Values = Count of DR_NO (Stacked Bar Chart).
Heatmap: Crime by Area and Time of Day: Rows = AREA NAME, Columns = Time Slot (6-hour bins), Values = Count of DR_NO (Excel Conditional Formatting in heatmap.xlsx).
Dashboard Features:

Charts Included: 7 of 8 (all except Heatmap) in dashboard.xlsx:
Crime by Area (B2)
Crime by Time (H20)
Crime by Weapon (H38)
Crime by Description (H2)
Case Status by Area (B38)
Crime by Age Group (B20)
Crime by Age Group & Sex (Y25)
Slicers:
AREA NAME: Filter by area (e.g., "Southeast").
Date: Filter by date range.
Vict Gender: Filter by gender (M, F, Unknown).
Hyperlinks: Added clickable navigation to:
Dashboard (internal sheet or dashboard.xlsx).
Heatmap (heatmap.xlsx).
Dataset (data/Crime_Data_from_2020_to_Present.csv).
Website (data.lacity.org).
Key Insights
Highest crime area: Southwest (based on initial analysis).
Most common crime: Battery - Simple Assault.
Peak crime hours: Evening (6 PM - 10 PM).
Tools Used
Microsoft Excel: Data cleaning, pivot tables, charts, slicers, and hyperlinks.
GitHub: Version control and project showcase.
