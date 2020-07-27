# Pig - Advance_2

## 1. Review the Pig Script
Change directories to the Preparing Data for Hive lab folder. View the contents of wh_visits.pig:



## 2. Store the Projection in the Hive Warehouse
Open wh_visits.pig. Add the following command at the bottom of the file, which stores the project_potus relation into a very specific folder in the Hive warehouse:
STORE project_potus INTO '/apps/hive/warehouse/wh_visits/';



## 3. Run the Pig Script
Save your changes to wh_visits.pig. Run the script from the command line:
pig wh_visits.pig



## 4. View the Results
a. The wh_visits.pig script creates a directory in the Hive warehouse named wh_visits. Use ls to view its contents:



b. View the contents of one of the result files. It should look like the following:



