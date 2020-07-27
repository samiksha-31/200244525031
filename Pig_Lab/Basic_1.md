# Pig - Basic_1

## 1. View the Raw Data
Unzip the archive in the /home/hadoop/labs/Lab5.1 folder, which contains a file named whitehouse_visits.txt and View the contents of this file:

![1](https://user-images.githubusercontent.com/63635471/88553652-2330ac00-d043-11ea-91b3-3f879a6e5137.PNG)


## 2. Load the Data into HDFS
a. Start the Grunt shell:

![2](https://user-images.githubusercontent.com/63635471/88553667-26c43300-d043-11ea-95b5-bfb8489891a1.PNG)

b. From the Grunt shell, make a new directory in HDFS named whitehouse:

![3](https://user-images.githubusercontent.com/63635471/88553669-27f56000-d043-11ea-8ed7-e8d1dc830de0.PNG)

c. Use the copyFromLocal command in the Grunt shell to copy the whitehouse_visits.txt file to the whitehouse folder in HDFS, renaming the file visits.txt. 
Use the ls command to verify that the file was uploaded successfully:

![4](https://user-images.githubusercontent.com/63635471/88553672-29268d00-d043-11ea-9749-c305646db153.PNG)


## 3. Define a Relation
a. You will use the TextLoader to load the visits.txt file. Use DESCRIBE to notice that A does not have a schema:

![5](https://user-images.githubusercontent.com/63635471/88553676-29bf2380-d043-11ea-9b84-52aa3c2aa1dd.PNG)

b. We want to get a sense of what this data looks like. Use the LIMIT operator to define a new relation named A_limit that is limited to 10 records of A.
Use the DUMP operator to view the A_limit relation.

![6](https://user-images.githubusercontent.com/63635471/88553678-2a57ba00-d043-11ea-8bcc-3b2ddd4bb04b.PNG)
![7](https://user-images.githubusercontent.com/63635471/88553685-2b88e700-d043-11ea-8c8d-af2c674210b8.PNG)


## 4. Define a Schema
a. Load the White House data again, but this time use the PigStorage loader and also define a partial schema.
Use the DESCRIBE command to view the schema:

![8](https://user-images.githubusercontent.com/63635471/88553695-2d52aa80-d043-11ea-8429-0d81576c1509.PNG)


## 5. The STORE Command
a. Enter the following STORE command, which stores the B relation into a folder named whouse_tab and separates the fields of each record with tabs:

![9](https://user-images.githubusercontent.com/63635471/88553700-2e83d780-d043-11ea-9723-ba60a04c4ed3.PNG)
![10](https://user-images.githubusercontent.com/63635471/88553708-2fb50480-d043-11ea-8ad5-e6b019e1a98b.PNG)

b. Verify that the whouse_tab folder was created:

![11](https://user-images.githubusercontent.com/63635471/88553711-304d9b00-d043-11ea-8a2c-f3ad038f5526.PNG)

c. View one of the output files to verify they contain the B relation in a tab-delimited format:

![12](https://user-images.githubusercontent.com/63635471/88553714-30e63180-d043-11ea-910f-63fbf0ee7f7d.PNG)


## 6. Use a Different Storer
a. In the previous step, you stored a relation using PigStorage with a tab delimiter. Enter the following command, which stores the same relation but in a JSON format:

![13](https://user-images.githubusercontent.com/63635471/88553719-33e12200-d043-11ea-9c22-8b6a0a620880.PNG)
![14](https://user-images.githubusercontent.com/63635471/88553723-35124f00-d043-11ea-9fe7-35b13d355c97.PNG)


b. Verify that the whouse_json folder was created:

![15](https://user-images.githubusercontent.com/63635471/88553725-36437c00-d043-11ea-8219-3a73dc483398.PNG)

c. View one of the output files:

![16](https://user-images.githubusercontent.com/63635471/88553727-36dc1280-d043-11ea-9de9-879b8c018efe.PNG)



