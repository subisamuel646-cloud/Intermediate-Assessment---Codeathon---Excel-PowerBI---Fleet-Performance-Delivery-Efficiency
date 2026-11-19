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
Rename the New table --> In the dataset displayed select the columns of the vehicle Master table needed--->ok



