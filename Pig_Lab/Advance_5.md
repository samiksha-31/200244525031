# Pig - Advance_5

## 1. Explore the Comments Field
a. From the Pig Grunt shell, start by loading visits.txt:



b. Field $25 is the comments. Filter out all records where field $25 is null.
Define a new relation that is a projection of only column $25.
View the schema of comments and make sure you understand how this relation ended up as a tuple with one field:



## 2. Test the Relation
Common Pig task is to test a relation to make sure it is consistent with what you are intending it to be. But using DUMP on a big data relation might take too long or not be practical, so define a SAMPLE of comments.
DUMP the comments_sample relation. The output should be non-null comments about visitors to the White House:



## 3. Count the Number of Comments
Write Pig statements that output the number of records in the comments relation. The correct result is 222,839 records:



## 4. Split the Dataset
a. In this step, you will split visits.txt into two datasets: those that contain “CONGRESS” in the comments field, and those that do not.
Use the SPLIT command to split the visits relation into two new relations named congress and not_congress.
Store the congress relation into a folder named ‘congress’:



b. Similarly, STORE the not_congress relation in a folder named ‘not_congress’:



c. View the output folders using ls:



d. View one of the output files in congress and make sure the string “CONGRESS” appears in the comment field:



## 5. Count the Results
Write Pig statements that output the number of records in the congress relation. This will tell us how many visitors to the White House have “CONGRESS” in the comments of their visit log. The correct result is 102:



