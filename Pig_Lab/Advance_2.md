# Pig - Advance_2

## 1. Review the Pig Script
Change directories to the Preparing Data for Hive lab folder. View the contents of wh_visits.pig:

![1](https://user-images.githubusercontent.com/63635471/88564528-f1264680-d050-11ea-8fb5-edb7d5254d37.PNG)


## 2. Store the Projection in the Hive Warehouse
Open wh_visits.pig. Add the following command at the bottom of the file, which stores the project_potus relation into a very specific folder in the Hive warehouse:
STORE project_potus INTO '/apps/hive/warehouse/wh_visits/';

![2](https://user-images.githubusercontent.com/63635471/88564532-f2577380-d050-11ea-8b6e-0952fa72e7b3.PNG)


## 3. Run the Pig Script
Save your changes to wh_visits.pig. Run the script from the command line:
pig wh_visits.pig

![3](https://user-images.githubusercontent.com/63635471/88564534-f388a080-d050-11ea-9d31-b98d4972d74a.PNG)

![4](https://user-images.githubusercontent.com/63635471/88564541-f5526400-d050-11ea-9722-d010f866a622.PNG)


## 4. View the Results
a. The wh_visits.pig script creates a directory in the Hive warehouse named wh_visits. Use ls to view its contents:

![5](https://user-images.githubusercontent.com/63635471/88564551-f71c2780-d050-11ea-93e6-f38d5f99686e.PNG)

b. View the contents of one of the result files. It should look like the following:

![6](https://user-images.githubusercontent.com/63635471/88564556-f84d5480-d050-11ea-9810-4754def1dbaf.PNG)

![7](https://user-images.githubusercontent.com/63635471/88564558-f8e5eb00-d050-11ea-8a63-12fe02c3a9e3.PNG)

