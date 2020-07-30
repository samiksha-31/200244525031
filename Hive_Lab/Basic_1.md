# Hive - Basic_1

## 1. Review the Data
a. Use the hdfs dfs -ls command to view the contents of the /apps/hive/warehouse/wh_visits/ folder in HDFS:

![1](https://user-images.githubusercontent.com/63635471/88940292-36db4d00-d2a5-11ea-82c4-e9696263b88d.PNG)


## 2. Define a Hive Script
a. In the /home/hadoop/labs/Lab7.1 folder, there is a text file named wh_visits.hive. View its contents.
it defines a Hive table named wh_visits with the following schema that matches the data in your project_potus folder:

![2](https://user-images.githubusercontent.com/63635471/88940297-380c7a00-d2a5-11ea-86b3-73bdd633d21e.PNG)

b. Run the script

![3](https://user-images.githubusercontent.com/63635471/88940301-38a51080-d2a5-11ea-84bf-0b3ebb1ef89e.PNG)


## 3. Verify the Table Creation
a. Start the Hive Shell:

![4](https://user-images.githubusercontent.com/63635471/88940303-38a51080-d2a5-11ea-9f69-4c6e852e3f6d.PNG)

b. From the hive> prompt, enter the “show tables” command:

![5](https://user-images.githubusercontent.com/63635471/88940304-393da700-d2a5-11ea-8716-67b084c9f7ff.PNG)

c. Use the describe command to view the details of wh_visits:

![6](https://user-images.githubusercontent.com/63635471/88940306-39d63d80-d2a5-11ea-913d-f67344517289.PNG)

d. Try running a query (even though the table is empty):

![7](https://user-images.githubusercontent.com/63635471/88940309-39d63d80-d2a5-11ea-8add-6e12a0eb29b2.PNG)


## 4. Count the Number of Rows in a Table
Enter the following Hive query, which outputs the number of rows in wh_visits:

![8](https://user-images.githubusercontent.com/63635471/88940317-3a6ed400-d2a5-11ea-9c84-86ff09403823.PNG)


## 5. Selecting the Input File Name
Hive has two virtual columns that get created automatically for every table:
INPUT__FILE__NAME and BLOCK__OFFSET__INSIDE__FILE.
The result of this query is visitors to the White House whose last name starts with “Y.”

![9](https://user-images.githubusercontent.com/63635471/88940318-3b076a80-d2a5-11ea-9c51-7de9d1942cec.PNG)


## 6. Drop a Table
a. Start by defining a simple table called names using the Hive Shell:

![10](https://user-images.githubusercontent.com/63635471/88940319-3ba00100-d2a5-11ea-8c80-458527d7e20e.PNG)

b. Use the Hive dfs command to put Lab7.1/names.txt into the table’s whitehouse folder:

![11](https://user-images.githubusercontent.com/63635471/88940320-3c389780-d2a5-11ea-8580-ffc66d33ce12.PNG)

c. From the Hive Shell, run the query:

![12](https://user-images.githubusercontent.com/63635471/88940322-3c389780-d2a5-11ea-97b1-40fe548da1f8.PNG)

![13](https://user-images.githubusercontent.com/63635471/88940323-3cd12e00-d2a5-11ea-896d-eec3e12846ba.PNG)

d. Now drop the names table:

![14](https://user-images.githubusercontent.com/63635471/88940325-3cd12e00-d2a5-11ea-9ce6-f352d38dd0dd.PNG)


## 7. Define an External Table
a. Start by putting names.txt into HDFS:

![15](https://user-images.githubusercontent.com/63635471/88940327-3d69c480-d2a5-11ea-8569-7132d3a34644.PNG)

b. Create a folder in HDFS for the external table to store its data in:

![16](https://user-images.githubusercontent.com/63635471/88940331-3d69c480-d2a5-11ea-8f43-421e67efede0.PNG)

![17](https://user-images.githubusercontent.com/63635471/88940335-3e025b00-d2a5-11ea-91f1-625c493ec00c.PNG)

c. Define the names table as external this time:

![18](https://user-images.githubusercontent.com/63635471/88940336-3e9af180-d2a5-11ea-9758-4d9497446548.PNG)

d. Load data into the table:

![19](https://user-images.githubusercontent.com/63635471/88940340-3e9af180-d2a5-11ea-9a4c-531ad5f28f1b.PNG)

e. Verify that the load worked:

![20](https://user-images.githubusercontent.com/63635471/88940344-3f338800-d2a5-11ea-81d6-62a877f5b06a.PNG)

f. Notice the names.txt file has been moved to /home/hadoop/hivedemo:

![21](https://user-images.githubusercontent.com/63635471/88940347-3fcc1e80-d2a5-11ea-9258-786733b23aca.PNG)

g. Now drop the names table:

![22](https://user-images.githubusercontent.com/63635471/88940349-4064b500-d2a5-11ea-9b28-e5c566858e04.PNG)

h. View the contents of /home/hadoop/hivedemo. Notice that names.txt is still there:

![23](https://user-images.githubusercontent.com/63635471/88940351-4064b500-d2a5-11ea-92a9-1de65a626e92.PNG)
