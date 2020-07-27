# Pig - Advance_5

## 1. Explore the Comments Field
a. From the Pig Grunt shell, start by loading visits.txt:

![1](https://user-images.githubusercontent.com/63635471/88568751-14ec8b00-d057-11ea-8b6c-0f3a284d0a5a.PNG)

b. Field $25 is the comments. Filter out all records where field $25 is null.
Define a new relation that is a projection of only column $25.
View the schema of comments and make sure you understand how this relation ended up as a tuple with one field:

![2](https://user-images.githubusercontent.com/63635471/88568754-15852180-d057-11ea-967c-a560a987115e.PNG)


## 2. Test the Relation
Common Pig task is to test a relation to make sure it is consistent with what you are intending it to be. But using DUMP on a big data relation might take too long or not be practical, so define a SAMPLE of comments.
DUMP the comments_sample relation. The output should be non-null comments about visitors to the White House:

![3](https://user-images.githubusercontent.com/63635471/88568756-161db800-d057-11ea-85b0-f93df66ec2db.PNG)

![4](https://user-images.githubusercontent.com/63635471/88568757-16b64e80-d057-11ea-8192-17d050be6205.PNG)


## 3. Count the Number of Comments
Write Pig statements that output the number of records in the comments relation. The correct result is 222,839 records:

![5](https://user-images.githubusercontent.com/63635471/88568758-16b64e80-d057-11ea-953c-3f20c68e6283.PNG)

![6](https://user-images.githubusercontent.com/63635471/88568761-174ee500-d057-11ea-8db5-0ee60015d054.PNG)


## 4. Split the Dataset
a. In this step, you will split visits.txt into two datasets: those that contain “CONGRESS” in the comments field, and those that do not.
Use the SPLIT command to split the visits relation into two new relations named congress and not_congress.
Store the congress relation into a folder named ‘congress’:

![7](https://user-images.githubusercontent.com/63635471/88568763-174ee500-d057-11ea-88a1-56f8b6403a09.PNG)

![8](https://user-images.githubusercontent.com/63635471/88568765-17e77b80-d057-11ea-93d3-d9c16b2e8de8.PNG)

b. Similarly, STORE the not_congress relation in a folder named ‘not_congress’:

![9](https://user-images.githubusercontent.com/63635471/88568766-18801200-d057-11ea-9ed4-622a58df146d.PNG)

![10](https://user-images.githubusercontent.com/63635471/88568768-18801200-d057-11ea-8027-d710e93a4519.PNG)

c. View the output folders using ls:

![11](https://user-images.githubusercontent.com/63635471/88568770-1918a880-d057-11ea-8ea3-27f25b79ee61.PNG)

d. View one of the output files in congress and make sure the string “CONGRESS” appears in the comment field:

![12](https://user-images.githubusercontent.com/63635471/88568773-19b13f00-d057-11ea-994c-748d103a7d2a.PNG)


## 5. Count the Results
Write Pig statements that output the number of records in the congress relation. This will tell us how many visitors to the White House have “CONGRESS” in the comments of their visit log. The correct result is 102:

![13](https://user-images.githubusercontent.com/63635471/88568775-1a49d580-d057-11ea-9b20-334ec05e4551.PNG)

![14](https://user-images.githubusercontent.com/63635471/88568777-1a49d580-d057-11ea-850d-402ec8015bc4.png)


