# **Sqoop Commands**

## *Importing RDBMS Data into HDFS*

1. Create table and import data in RDBMS:

![2 1](https://user-images.githubusercontent.com/63635471/88174741-6ef9e480-cc42-11ea-8ac1-ef50b5b047b7.png)

![2 2](https://user-images.githubusercontent.com/63635471/88174743-70c3a800-cc42-11ea-9e95-633bce3e055f.png)

![2 3](https://user-images.githubusercontent.com/63635471/88174745-70c3a800-cc42-11ea-9125-52febdbd347f.png)

![2 4](https://user-images.githubusercontent.com/63635471/88174747-715c3e80-cc42-11ea-9b55-7905a89c1477.png)

![2 5](https://user-images.githubusercontent.com/63635471/88174752-728d6b80-cc42-11ea-92e3-47cfe46a4150.png)

![2 6](https://user-images.githubusercontent.com/63635471/88174755-73260200-cc42-11ea-9b59-1c090c6bf237.png)

![2 7](https://user-images.githubusercontent.com/63635471/88174758-73be9880-cc42-11ea-9243-066274fe9a85.png)

![2 8](https://user-images.githubusercontent.com/63635471/88174759-74572f00-cc42-11ea-9a9e-c632767b6875.png)


2. Create hadoop cluster with sqoop:

![2 9](https://user-images.githubusercontent.com/63635471/88174761-75885c00-cc42-11ea-95a8-5ce72360970a.png)

![2 10](https://user-images.githubusercontent.com/63635471/88174764-7620f280-cc42-11ea-9360-c9bf7b805cda.png)

![2 11](https://user-images.githubusercontent.com/63635471/88174765-76b98900-cc42-11ea-8376-ec78a242f1d3.png)

![2 12](https://user-images.githubusercontent.com/63635471/88174770-77eab600-cc42-11ea-9328-28b0c2b604c6.png)

![2 13](https://user-images.githubusercontent.com/63635471/88174773-78834c80-cc42-11ea-985f-b1e91b09f1e2.png)


3. Import the Table into HDFS:

![1](https://user-images.githubusercontent.com/63635471/88174960-c730e680-cc42-11ea-93ca-4ca74f3dd591.PNG)

![2](https://user-images.githubusercontent.com/63635471/88174963-c8faaa00-cc42-11ea-99c2-363f095d8fb4.PNG)

4. Verify the Import:

![3](https://user-images.githubusercontent.com/63635471/88174964-c9934080-cc42-11ea-8b07-cef760a82a1b.PNG)

![4](https://user-images.githubusercontent.com/63635471/88174967-c9934080-cc42-11ea-92c4-a9066dd1c814.PNG)

![5](https://user-images.githubusercontent.com/63635471/88174971-ca2bd700-cc42-11ea-9221-263c60105f53.PNG)

![6](https://user-images.githubusercontent.com/63635471/88174972-cac46d80-cc42-11ea-962d-17875beec2ef.PNG)

![7](https://user-images.githubusercontent.com/63635471/88174973-cb5d0400-cc42-11ea-956b-c39bd43f8352.PNG)


5. Specify Columns to Import:

![8](https://user-images.githubusercontent.com/63635471/88174975-cb5d0400-cc42-11ea-8f6f-575271e6cd0c.PNG)

![9](https://user-images.githubusercontent.com/63635471/88174976-cbf59a80-cc42-11ea-9644-1b96fcd3163b.PNG)

![10](https://user-images.githubusercontent.com/63635471/88174978-cc8e3100-cc42-11ea-9288-85c7ae094dde.PNG)

![11](https://user-images.githubusercontent.com/63635471/88174979-cd26c780-cc42-11ea-8de7-e0b2858e92a9.PNG)


6. Importing from a Query:

![2 14](https://user-images.githubusercontent.com/63635471/88174777-791be300-cc42-11ea-81cb-461241e4ec54.png)

![2 15](https://user-images.githubusercontent.com/63635471/88174780-7a4d1000-cc42-11ea-9b23-3a842d10c1cc.png)

![2 16](https://user-images.githubusercontent.com/63635471/88174791-7c16d380-cc42-11ea-8a32-443e7a90779f.png)

![2 17](https://user-images.githubusercontent.com/63635471/88174795-7caf6a00-cc42-11ea-9ff8-3572de8d32cc.png)

![2 18](https://user-images.githubusercontent.com/63635471/88174802-7e792d80-cc42-11ea-98f2-d14277d8d160.png)

![2 19](https://user-images.githubusercontent.com/63635471/88174803-7faa5a80-cc42-11ea-9e89-f65151f0cc61.png)



# *Exporting HDFS Data to an RDBMS*

1. Create the table salaries2 in database:

![2 20](https://user-images.githubusercontent.com/63635471/88174807-8042f100-cc42-11ea-90c5-4f8fea19ebc3.png)


2. Put the Data into HDFS:

![12](https://user-images.githubusercontent.com/63635471/88174980-cd26c780-cc42-11ea-801d-c929ba741922.PNG)

![13](https://user-images.githubusercontent.com/63635471/88174982-cdbf5e00-cc42-11ea-817d-9eb9022904bf.PNG)

![14](https://user-images.githubusercontent.com/63635471/88174983-ce57f480-cc42-11ea-836b-5446a76cef08.PNG)

![15](https://user-images.githubusercontent.com/63635471/88174987-cef08b00-cc42-11ea-9d5f-e36d8c862d2a.PNG)

![16](https://user-images.githubusercontent.com/63635471/88174988-cef08b00-cc42-11ea-9f71-327b164f971a.PNG)


3. Export the Data:

![17](https://user-images.githubusercontent.com/63635471/88174989-cf892180-cc42-11ea-97d5-6c9cf7687f40.PNG)

![18](https://user-images.githubusercontent.com/63635471/88174993-d021b800-cc42-11ea-805e-7eeb77622b84.PNG)


4. Verify it worked by viewing the table’s contents from the mysql:

![2 21](https://user-images.githubusercontent.com/63635471/88174809-81741e00-cc42-11ea-86f6-1d16461a708d.png)

