# Pig - Advance_1

## 1. If you are in the Grunt shell, exit it using the quit command. In this lab, you will write a Pig script in a text file:



## 2. Upload the Congress Data
Put the file /root/devph/labs/Lab6.2/congress.txt into the whitehouse directory in HDFS:
Use the hdfs dfs -ls command to verify that the congress.txt file is in whitehouse, and use hdfs dfs -cat to view its contents. The file contains the names of and other information about the members of the U.S. Congress:



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

c. Notice the statistics output has “HASH_JOIN” underneath the “Features” column, which means a hash join was used to join the two datasets.


## 8. View the Results
a. The output will be in the joinresult folder in HDFS. Verify that the folder was created:



b. View the resulting file:



## 9. Try Using Replicated on the Join
a. Delete the joinresult directory in HDFS:



b. Modify your JOIN statement in join.pig so that is uses replication. It should look like this:
join_contact_congress = JOIN visitors BY (lname,fname),
congress_data BY (lname,fname) USING 'replicated';

c. Save your changes to join.pig and run the script again.
pig join.pig



d. Notice this time that the statistics output shows Pig used a “REPLICATED_JOIN” instead of a “HASH_JOIN”:



## 10. Count the Results
a. In join.pig, comment out the STORE command:
--STORE join_contact_congress INTO 'joinresult';

b. Notice in the output of your join.pig script that we know which party the visitor belongs to: Democrat, Republican, or Independent. Using the join_contact_congress:

c. Name the relation counters and use
the DUMP command to output the results:
join_group = GROUP join_contact_congress
BY congress_data::party;
counters = FOREACH join_group GENERATE group,
COUNT(join_contact_congress);
DUMP counters;

d. At the end of join.pig, add the following statement:
EXPLAIN counters;

Final output:


