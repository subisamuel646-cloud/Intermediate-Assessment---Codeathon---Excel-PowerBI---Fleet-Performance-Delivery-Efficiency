# Intermediate-Assessment---Codeathon---Excel-PowerBI---Fleet-Performance-Delivery-Efficiency
Data Cleaning & Modeling: (5marks)


Columns in Trip_Data :Trip_ID, Vehicle_ID, Driver_ID, Origin, Destination, Distance_km, Fuel_Consumed_L, Delivery_Status, Delivery_Date
Columns in Vehicle_Master : Vehicle_ID, Vehicle_Type, Capacity_kg, Maintenance_Cost
----> For Trip_Data, Make the First column as Trip_ID and remove the unwanted row data and make reasonable data T001 ---  T012
----> For Trip_Data in Distance_km column, 116+66 Replaced by adding both values
----> For both tables, Changed types, Formatted the data 

○	Fix missing fuel consumption values (use avg. per vehicle type).

Sol: Didnt find any missing fuel consumption values in the dataset

○	Relate Trips with Vehicle Master.

Sol: In Power Query of Excel, used Merge Queries
MergeQueries -----> Select both the tables from Queries pane ---> Merge Queries as New --> Trips table and Vehicle ID highlight ---> Vehicle Master and Vehicle ID highlight ---> Left Outer then Ok
Rename the New table "Logistics&Transportation" --> In the dataset displayed select the columns of the vehicle Master table needed--->ok


2. DAX Measures:  (5marks)

NOTE: Below are done in the new table "Logistics&Transportation"
○	Fuel Efficiency = Distance / Fuel Consumed

Sol:  Every vehicle has different distance covered so we will create as a new column for each individual trip
Fuel_Efficiency_Trip_km/L = DIVIDE('Logistics&Transportation'[Distance_km],'Logistics&Transportation'[Fuel_Consumed_L],0)

○	On-Time Delivery % = On-Time Trips / Total Trips

Sol: We need to calculate as New Measure
On-Time Trips : need to count the Trip_ID where the Delivery_Status is "On-Time"
Total Trips : need to count the Trip_ID 
On-Time Delivery % = DIVIDE(CALCULATE(COUNT('Logistics&Transportation'[Trip_ID]),'Logistics&Transportation'[Delivery_Status] = "On-Time"),COUNT('Logistics&Transportation'[Trip_ID]),0)

○	Cost per km = (Fuel Cost + Maintenance Cost) / Distance

Sol: We need to calculate as New Measure
Considering the Fuel Cost = 95
Cost per km = DIVIDE((SUM('Logistics&Transportation'[Fuel_Consumed_L]) * 95) + SUM('Logistics&Transportation'[Maintenance_Cost]), SUM('Logistics&Transportation'[Distance_km]), 0)

3. Visualization:  (5marks)
○	Bar chart: On-Time Delivery % by Route.

Sol:  For Route we need to combine 2 columns i.e Origin and destination
Data pane, go to Table tools (or Modeling), click New column
New column Route = 'Logistics&Transportation'[Origin] & "--" & 'Logistics&Transportation'[Destination]

In report view, click on Stacked Bar Chart --> Y axis : Route ,  X axis : On-Time Delivery% --> Format


○	Line chart: Fuel Efficiency trend by month.

Sol: In report view, click on Line Chart --> Y axis : Fuel_Efficiency_Trip(km/l) ,  X axis : Delivery_Date . As we pull the column it shows as a Date Hierarchy where we can limit to "Month" only as Year is 2023 for all --> Format

○	KPI cards: Avg. Delivery Time, Cost per km.

Sol: Add KPI Cards ---> Drag and Drop "Cost per km" and "On-Time delivery%" ---> Format

○	Map visual: Delivery performance by route (Origin → Destination).

Sol:  Add map visual (Best is Flow Map but I doesnot have it in my PowerBI) --> Location : Route , Bubble Size : On-Time Delivery% ---> Format

Expected Output: A transport operations dashboard to optimize routes and fleet usage.

Dashboard : In a sheet copy and paste all the above visualizations and then format accordingly.
