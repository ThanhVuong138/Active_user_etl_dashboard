# Active_user_etl_dashboard![Architechture](https://github.com/ThanhVuong138/Active_user_etl_dashboard/assets/106426014/4bd59ec8-dbf5-400f-bef8-bf6f2ed4770f)
Project Description:
1. Requirements:
- Inputs: Tables stored in the Data Warehouse system, including tables for vehicle sales information, customer information for vehicle purchases, customer information for service usage, and service invoice information.
- Outputs: Build a dynamic dashboard that automatically updates monthly data continuously for the past 10 years. The dashboard should display the number of customers visiting to purchase vehicles (UIO) and the number of customers registering for service usage after purchasing a vehicle within one year from 2022-2023 (Active) for the entire store system. The dashboard should allow viewing the results for any store. Calculate the Active/UIO ratio to observe the monthly active customer rate. This serves as a basis to understand the business situation of individual stores as well as the entire system, provide strategies and competition among stores, and timely detect anomalies for appropriate solutions.

2. ETL Implementation Process:
- Build a data synchronization process from the Data Warehouse source (PL/SQL, data for the entire system) to the SQL Server Data Mart (specialized data for the analysis team) using SSIS:
  + Use the ODAC API (Oracle) to connect databases together, using code in the script file Migrate_sql.txt to synchronize data as desired.
  + Set up the entire data synchronization process in the SQL Agent Jobs schedule on the first day of each month.
- Build a procedure to process the synchronized data from the stored tables after synchronization is complete and run the procedure on a schedule:
  + Use the code in the file PROCEDURE_ANALYTICS_CODE.txt to create a procedure and store it in a target table named Result.
  + Execute the procedure when running SSIS.

3. Dashboard Design:
- Design a dashboard to display the required output data as shown in the Dashboard.pdf file, linking it with the processed data sources in step 2.
- Set up data refresh time on Tableau according to the schedule on the first day of each month after the synchronization and data processing processes are completed.
