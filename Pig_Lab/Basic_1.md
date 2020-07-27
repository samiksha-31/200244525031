# Pig - Basic_1

## 1. View the Raw Data
Unzip the archive in the /home/hadoop/labs/Lab5.1 folder, which contains a file named whitehouse_visits.txt and View the contents of this file:


## 2. Load the Data into HDFS
a. Start the Grunt shell:



b. From the Grunt shell, make a new directory in HDFS named whitehouse:



c. Use the copyFromLocal command in the Grunt shell to copy the whitehouse_visits.txt file to the whitehouse folder in HDFS, renaming the file visits.txt. 
Use the ls command to verify that the file was uploaded successfully:



## 3. Define a Relation
a. You will use the TextLoader to load the visits.txt file. Use DESCRIBE to notice that A does not have a schema:



b. We want to get a sense of what this data looks like. Use the LIMIT operator to define a new relation named A_limit that is limited to 10 records of A.
Use the DUMP operator to view the A_limit relation.



## 4. Define a Schema
a. Load the White House data again, but this time use the PigStorage loader and also define a partial schema.
Use the DESCRIBE command to view the schema:



## 5. The STORE Command
a. Enter the following STORE command, which stores the B relation into a folder named whouse_tab and separates the fields of each record with tabs:



b. Verify that the whouse_tab folder was created:


c. View one of the output files to verify they contain the B relation in a tab-delimited format:



## 6. Use a Different Storer
a. In the previous step, you stored a relation using PigStorage with a tab delimiter. Enter the following command, which stores the same relation but in a JSON format:



b. Verify that the whouse_json folder was created:



c. View one of the output files:





