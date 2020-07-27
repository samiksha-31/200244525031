# Pig - Basic_2

## 1. Load the White House Visitor Data
Use the TextLoader to load the visits.txt file. From the Pig Grunt shell, define the following LOAD relation:

![1](https://user-images.githubusercontent.com/63635471/88555498-8d4a5080-d045-11ea-8ae1-cd4f653434a7.PNG)


## 2. Count the Number of Lines
a. Define a new relation named B that is a group of all the records in A.
Use DESCRIBE to view the schema of B:

![2](https://user-images.githubusercontent.com/63635471/88555504-8de2e700-d045-11ea-90fe-58d5a9d0c4d0.PNG)

b. The A field of the B tuple is a bag of all of the records in visits.txt. Use the COUNT function on this bag to determine how many lines of text are in visits.txt.
Use DUMP on A_count to view the result. The output should look like:

![3](https://user-images.githubusercontent.com/63635471/88555508-8e7b7d80-d045-11ea-875f-a1cf145d453e.PNG)
![4](https://user-images.githubusercontent.com/63635471/88555512-8f141400-d045-11ea-8930-8544e5952d40.PNG)


## 3. Analyze the Data’s Contents
a. Load the data using PigStorage(‘,’).
Use a FOREACH...GENERATE command to define a relation that is a projection of
the first 10 fields of the visits relation.

![5](https://user-images.githubusercontent.com/63635471/88555520-90ddd780-d045-11ea-88f7-5b74ec9921cf.PNG)

b. Use LIMIT to display only 50 records then DUMP the result.
The output should be 50 tuples that represent the first 10 fields of visits:

![6](https://user-images.githubusercontent.com/63635471/88555522-91766e00-d045-11ea-8bbe-93155c4f4e85.PNG)
![7](https://user-images.githubusercontent.com/63635471/88555525-920f0480-d045-11ea-911b-3f3ea72d84cb.PNG)


## 4. Locate the POTUS (President of the United States of America)
a. There are 26 fields in each record, and one of them represents the visitee (the person being visited in the White House). Your goal now is to locate this column and determine who has visited the President of the United States. Define a relation that is a projection of the last seven fields ($19 to $25) of visits. Use LIMIT to only output 500 records:

![8](https://user-images.githubusercontent.com/63635471/88555531-94715e80-d045-11ea-8c1c-86ba1ca28d56.PNG)

![9](https://user-images.githubusercontent.com/63635471/88555533-9509f500-d045-11ea-849a-7e6fb4037e64.PNG)

b. Use FILTER to define a relation that only contains records of visits where field $19 matches POTUS. Limit the output to 500 records. The output should include only visitors who met with the President:

![10](https://user-images.githubusercontent.com/63635471/88555538-95a28b80-d045-11ea-83fc-7df275579bc7.PNG)
![11](https://user-images.githubusercontent.com/63635471/88555544-96d3b880-d045-11ea-8f80-842bd4e7e13d.PNG)


## 5. Count the POTUS Visitors
Let’s discover how many people have visited the President. To do this, we need to count the number of records in visits where field $19 matches POTUS. See if you can write a Pig script to accomplish this. Use the potus relation from the previous step as a starting point. You will need to use GROUP ALL and then a FOREACH projection that uses the COUNT function.
If successful, you should get 21,819 as the number of visitors to the White House who visited the President:

![12](https://user-images.githubusercontent.com/63635471/88555548-9804e580-d045-11ea-9cc6-c5819cd219da.PNG)
![13](https://user-images.githubusercontent.com/63635471/88555554-99361280-d045-11ea-8221-25d0634e5eaa.PNG)


## 6. Finding People Who Visited the President
a. FILTER the relation by visitors who met with the President.
Define a projection of the potus relationship that contains the name and time of arrival of the visitor.
Order the potus_details projection by last name.
Store the records of potus_details_ordered into a folder named potus and using a comma delimiter:

![14](https://user-images.githubusercontent.com/63635471/88555564-99cea900-d045-11ea-8420-b009b99308c0.PNG)
![15](https://user-images.githubusercontent.com/63635471/88555573-9b986c80-d045-11ea-9a07-e76caaaf1b1b.PNG)

b. View the contents of the potus folder.
Notice that there is a single output file, so the Pig job was executed with one reducer. View the contents of the output file using cat:

![16](https://user-images.githubusercontent.com/63635471/88555576-9c310300-d045-11ea-805b-442137767569.PNG)

![17](https://user-images.githubusercontent.com/63635471/88555579-9d623000-d045-11ea-8a54-99150584d1b7.PNG)





