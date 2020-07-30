# Hive - Basic_2

## 1. Find the First Visit
a. create a new text file named whitehouse.hive with following commands and save it in your /home/hadoop/labs/Lab7.2 folder:
select * from wh_visits where time_of_arrival != ""
order by unix_timestamp(time_of_arrival,
'MM/dd/yyyy hh:mm')
limit 10;



b. Execute the script whitehouse.hive and wait for the results to be displayed:



c. The results should be 10 visitors, and the first visit should be in 2009, since that is when the dataset begins. The first visitors are Charles Kahn and Carol Keehan on 3/5/2009:


## 2. Find the Last Visit
a. Take the previous query and reverse the order by adding desc to the order by clause:

b. Run the query again, and you should see that the most recent visit was Jackie Walker on 3/18/2011.




## 3. Find the Most Common Comment
a. Create a new text file named comments.hive and save it in home/hadoop/labs/Lab7.2 folder.
You will now create a query that displays the 10 most frequently occurring comments. Start with the following select clause:
from wh_visits
select count(*) as comment_count, info_comment

b. Group the results of the query by the info_comment column:
group by info_comment

c. Order the results by comment_count, because we are only interested in comments that appear most frequently:
order by comment_count DESC

d. We only want the top results, so limit the result set to 10:
limit 10;

e. Save your changes to comments.hive and execute the script:



f. It appears that a blank comment is the most frequent comment, followed by the HOLIDAY BALL, then a variation of other receptions.

g. Modify the query so that it ignores empty comments:
where info_comment != ""

h. Re-run the script:




## 4. Least Frequent Comment
a. Run the previous query again, but this time, find the 10 least occurring comments.
order by comment_count

b. Save the changes and re-run the query:




## 5. Analyze the Data Inconsistencies
a. Modify the query in comments.hive. Instead of searching for empty comments. Search for comments that contain variations of the string “GEN RECEP.”:
where info_comment rlike '.*GEN.*\\s+RECEP.*'

b. Change the limit clause from 10 to 30:
limit 30;

c. Run the query again.
Notice there are several GENERAL RECEPTION entries that only differ by a number at the end or use the GEN RECEP abbreviation:



d. Try one more query to try and narrow GENERAL RECEPTION visit. Modify the WHERE clause in comments.hive to include “%GEN%”:
where info_comment like "%RECEP%"
and info_comment like "%GEN%"

e. Run the query again:



f. The output this time reveals all the variations of GEN and RECEP. Next, let’s add up the total number of them by running the following query:
from wh_visits
select count(*)
where info_comment like "%RECEP%"
and info_comment like "%GEN%";

g. Save the changes and run the query again.
Notice there are 2,697 visits to the POTUS with GEN RECEP in the comment field, which is about 12% of the 21,819 total visits to the POTUS in our dataset:




## 6. Verify the Result
a. Modify the query from the last step and display the top 30 comments that contain “WHO” and “EOP.”
select count(*) as comment_count, info_count
where info_comment like "%WHO%"
and info_comment like "%EOP%"
order by comment_count DESC;

b. Save the changes and run the query again:



c. Modify the script again, this time to run a query that counts the number of records with WHO and EOP in the comments, and run the query:



You should get 1,687 visits, or 7.7% of the visitors to the POTUS.


## 7. Find the Most Visits
Write a Hive script that finds the top 20 individuals who visited the POTUS most.
from wh_visits
select count(*) as most_visit, fname, lname
group by fname, lname
order by most_visit DESC
limit 20;

