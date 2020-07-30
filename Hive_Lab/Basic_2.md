# Hive - Basic_2

## 1. Find the First Visit
a. Create a new text file named whitehouse.hive with following commands and save it in your /home/hadoop/labs/Lab7.2 folder:
select * from wh_visits where time_of_arrival != ""
order by unix_timestamp(time_of_arrival,
'MM/dd/yyyy hh:mm')
limit 10;

![1](https://user-images.githubusercontent.com/63635471/88948610-c4bc3580-d2af-11ea-97b1-716acfb391b7.PNG)

b. Execute the script whitehouse.hive and wait for the results to be displayed:

![2](https://user-images.githubusercontent.com/63635471/88948618-c5ed6280-d2af-11ea-8c4b-a8d04f5ef069.PNG)

c. The results should be 10 visitors, and the first visit should be in 2009, since that is when the dataset begins. The first visitors are Charles Kahn and Carol Keehan on 3/5/2009.


## 2. Find the Last Visit
a. Take the previous query and reverse the order by adding desc to the order by clause.

b. Run the query again, and you should see that the most recent visit was Jackie Walker on 3/18/2011.

![3](https://user-images.githubusercontent.com/63635471/88948620-c685f900-d2af-11ea-8683-dc9de40eeac0.PNG)


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

![4](https://user-images.githubusercontent.com/63635471/88948623-c71e8f80-d2af-11ea-9c87-40122b9da91c.PNG)

f. It appears that a blank comment is the most frequent comment, followed by the HOLIDAY BALL, then a variation of other receptions.

g. Modify the query so that it ignores empty comments:
where info_comment != ""

h. Re-run the script:

![5](https://user-images.githubusercontent.com/63635471/88948625-c7b72600-d2af-11ea-8190-97c946715987.PNG)


## 4. Least Frequent Comment
a. Run the previous query again, but this time, find the 10 least occurring comments.
order by comment_count

b. Save the changes and re-run the query:

![6](https://user-images.githubusercontent.com/63635471/88948626-c84fbc80-d2af-11ea-90ce-fd9dd29f1e3b.PNG)


## 5. Analyze the Data Inconsistencies
a. Modify the query in comments.hive. Instead of searching for empty comments. Search for comments that contain variations of the string “GEN RECEP.”:
where info_comment rlike '.*GEN.*\\s+RECEP.*'

b. Change the limit clause from 10 to 30:
limit 30;

c. Run the query again.
Notice there are several GENERAL RECEPTION entries that only differ by a number at the end or use the GEN RECEP abbreviation:

![7](https://user-images.githubusercontent.com/63635471/88948629-c84fbc80-d2af-11ea-9752-ca33f454e071.PNG)

d. Try one more query to try and narrow GENERAL RECEPTION visit. Modify the WHERE clause in comments.hive to include “%GEN%”:
where info_comment like "%RECEP%"
and info_comment like "%GEN%"

e. Run the query again:

![8](https://user-images.githubusercontent.com/63635471/88948633-c8e85300-d2af-11ea-8589-c47b5b71ebcf.PNG)

f. The output this time reveals all the variations of GEN and RECEP. Next, let’s add up the total number of them by running the following query:
from wh_visits
select count(*)
where info_comment like "%RECEP%"
and info_comment like "%GEN%";

g. Save the changes and run the query again.
Notice there are 2,697 visits to the POTUS with GEN RECEP in the comment field, which is about 12% of the 21,819 total visits to the POTUS in our dataset:

![9](https://user-images.githubusercontent.com/63635471/88948635-c980e980-d2af-11ea-9717-275399529d1f.PNG)


## 6. Verify the Result
a. Modify the query from the last step and display the top 30 comments that contain “WHO” and “EOP.”
select count(*) as comment_count, info_count
where info_comment like "%WHO%"
and info_comment like "%EOP%"
order by comment_count DESC;

b. Save the changes and run the query again:

![10](https://user-images.githubusercontent.com/63635471/88948637-c980e980-d2af-11ea-85ce-eef2d63c12e5.PNG)

c. Modify the script again, this time to run a query that counts the number of records with WHO and EOP in the comments, and run the query:

![11](https://user-images.githubusercontent.com/63635471/88948640-ca198000-d2af-11ea-9c70-449235aef2c2.PNG)

You should get 1,687 visits, or 7.7% of the visitors to the POTUS.


## 7. Find the Most Visits
Write a Hive script that finds the top 20 individuals who visited the POTUS most.
from wh_visits
select count(*) as most_visit, fname, lname
group by fname, lname
order by most_visit DESC
limit 20;

![12](https://user-images.githubusercontent.com/63635471/88948641-cab21680-d2af-11ea-9187-d1fbb2de8064.PNG)

![13](https://user-images.githubusercontent.com/63635471/88948644-cab21680-d2af-11ea-993f-ea74729b50c2.PNG)

