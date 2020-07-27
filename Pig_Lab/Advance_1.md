# Pig - Advance_1

## 1. If you are in the Grunt shell, exit it using the quit command. In this lab, you will write a Pig script in a text file:

![1](https://user-images.githubusercontent.com/63635471/88557028-570dd080-d047-11ea-80a7-6278307daac0.PNG)


## 2. Upload the Congress Data
Put the file /home/hadoop/labs/Lab6.2/congress.txt into the whitehouse directory in HDFS:
Use the hdfs dfs -ls command to verify that the congress.txt file is in whitehouse, and use hdfs dfs -cat to view its contents. The file contains the names of and other information about the members of the U.S. Congress:

![2](https://user-images.githubusercontent.com/63635471/88557035-59702a80-d047-11ea-9f62-075b67780df3.PNG)
![3](https://user-images.githubusercontent.com/63635471/88557036-5a08c100-d047-11ea-8ba4-f09b1c10d5cf.PNG)

## 3. Create a Pig Script File
a. Enter the script in a text file.

b. At the top of the file, add a comment:
--join.pig: joins congress.txt and visits.txt

## 4. Load the White House Visitors
Define the following visitors relations, which will contain the first and last names of all White House visitors:
visitors = LOAD 'whitehouse/visits.txt' USING PigStorage(',') AS (lname:chararray, fname:chararray);
That is the only data we are going to use from visits.txt.

## 5. Define a Projection of the Congress Data
a. Add the following load command that loads the ‘congress.txt’ file into a relation named congress. The data is tab-delimited, so no special Pig loader is needed:
congress = LOAD 'whitehouse/congress.txt' AS (
full_title:chararray,
district:chararray,
title:chararray,
fname:chararray,
lname:chararray,
party:chararray
);

b. The names in visits.txt are all uppercase, but the names in congress.txt are not.
Define a projection of the congress relation that consists of the following fields:
congress_data = FOREACH congress GENERATE
district,
UPPER(lname) AS lname,
UPPER(fname) AS fname,
party;

## 6. Join the Two Datasets
a. Define a new relation named join_contact_congress that is a JOIN of visitors
and congress_data. Perform the join on both the first and last names.

b. Use the STORE command to store the result of join_contact_congress into a
directory named ‘joinresult’.

Solution:
join_contact_congress = JOIN visitors BY (lname,fname),
congress_data BY (lname,fname);
STORE join_contact_congress INTO 'joinresult';

## 7. Run the Pig Script
a. Save your changes to join.pig.

b. Run the script using the following command:
pig join.pig

![4](https://user-images.githubusercontent.com/63635471/88557051-5ecd7500-d047-11ea-8fbe-90ae12701ec4.PNG)

![6](https://user-images.githubusercontent.com/63635471/88557066-62f99280-d047-11ea-8347-114308fc2796.PNG)

![13](https://user-images.githubusercontent.com/63635471/88557097-6ab93700-d047-11ea-9566-4c7c46f6edcc.PNG)

c. Notice the statistics output has “HASH_JOIN” underneath the “Features” column, which means a hash join was used to join the two datasets.

![5](https://user-images.githubusercontent.com/63635471/88557061-61c86580-d047-11ea-94f9-9d8e34fe6ac0.PNG)


## 8. View the Results
a. The output will be in the joinresult folder in HDFS. Verify that the folder was created:

![7](https://user-images.githubusercontent.com/63635471/88557071-642abf80-d047-11ea-9a37-f8cc3cca97db.PNG)


b. View the resulting file:

![8](https://user-images.githubusercontent.com/63635471/88557073-65f48300-d047-11ea-9975-0561dddd3f6f.PNG)


## 9. Try Using Replicated on the Join
a. Delete the joinresult directory in HDFS:

![9](https://user-images.githubusercontent.com/63635471/88557082-6856dd00-d047-11ea-8a7c-f201b4866c1a.PNG)

b. Modify your JOIN statement in join.pig so that is uses replication. It should look like this:
join_contact_congress = JOIN visitors BY (lname,fname),
congress_data BY (lname,fname) USING 'replicated';

c. Save your changes to join.pig and run the script again.
pig join.pig

![10](https://user-images.githubusercontent.com/63635471/88557086-68ef7380-d047-11ea-93aa-537aeef51f24.PNG)

![12](https://user-images.githubusercontent.com/63635471/88557095-6a20a080-d047-11ea-8f58-8840a3098e9f.PNG)

![14](https://user-images.githubusercontent.com/63635471/88557101-6bea6400-d047-11ea-88f1-877c5064f032.PNG)

d. Notice this time that the statistics output shows Pig used a “REPLICATED_JOIN” instead of a “HASH_JOIN”:

![11](https://user-images.githubusercontent.com/63635471/88557090-69880a00-d047-11ea-96ad-df7d6d27b219.PNG)


## 10. Count the Results
a. In join.pig, comment out the STORE command:
--STORE join_contact_congress INTO 'joinresult';

b. Notice in the output of your join.pig script that we know which party the visitor belongs to: Democrat, Republican, or Independent. Using the join_contact_congress:

c. Name the relation counters and use the DUMP command to output the results:
join_group = GROUP join_contact_congress
BY congress_data::party;
counters = FOREACH join_group GENERATE group,
COUNT(join_contact_congress);
DUMP counters;

d. At the end of join.pig, add the following statement:
EXPLAIN counters;

Final output:

![15](https://user-images.githubusercontent.com/63635471/88557105-6c82fa80-d047-11ea-8c9e-f4247ee46cc1.PNG)

