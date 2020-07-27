# Pig - Basic_2

## 1. Load the White House Visitor Data
Use the TextLoader to load the visits.txt file. From the Pig Grunt shell, define the following LOAD relation:



## 2. Count the Number of Lines
a. Define a new relation named B that is a group of all the records in A.
Use DESCRIBE to view the schema of B:



b. The A field of the B tuple is a bag of all of the records in visits.txt. Use the COUNT function on this bag to determine how many lines of text are in visits.txt.
Use DUMP on A_count to view the result. The output should look like:



## 3. Analyze the Data’s Contents
a. Load the data using PigStorage(‘,’).
Use a FOREACH...GENERATE command to define a relation that is a projection of
the first 10 fields of the visits relation.



b. Use LIMIT to display only 50 records then DUMP the result.
The output should be 50 tuples that represent the first 10 fields of visits:



## 4. Locate the POTUS (President of the United States of America)
a. There are 26 fields in each record, and one of them represents the visitee (the person being visited in the White House). Your goal now is to locate this column and determine who has visited the President of the United States. Define a relation that is a projection of the last seven fields ($19 to $25) of visits. Use LIMIT to only output 500 records:



b. Use FILTER to define a relation that only contains records of visits where field $19 matches POTUS. Limit the output to 500 records. The output should include only visitors who met with the President:



## 5. Count the POTUS Visitors
Let’s discover how many people have visited the President. To do this, we need to count the number of records in visits where field $19 matches POTUS. See if you can write a Pig script to accomplish this. Use the potus relation from the previous step as a starting point. You will need to use GROUP ALL and then a FOREACH projection that uses the COUNT function.
If successful, you should get 21,819 as the number of visitors to the White House who visited the President:



## 6. Finding People Who Visited the President
a. FILTER the relation by visitors who met with the President.
Define a projection of the potus relationship that contains the name and time of arrival of the visitor.
Order the potus_details projection by last name.
Store the records of potus_details_ordered into a folder named potus and using a comma delimiter:



b. View the contents of the potus folder.
Notice that there is a single output file, so the Pig job was executed with one reducer. View the contents of the output file using cat:










