# Pig - Advance_3

## 1. View the Clickstream Data
a. Open a Terminal and change directories. View the contents of clicks.csv:

![1](https://user-images.githubusercontent.com/63635471/88565655-8fff7280-d052-11ea-82a6-ba12c086c387.PNG)

b. Put the file in HDFS.

![2](https://user-images.githubusercontent.com/63635471/88565661-91309f80-d052-11ea-825d-4512b1fa3012.PNG)

c. Download the datafu-pig-1.6.0.jar and piggybank.jar files:

![3](https://user-images.githubusercontent.com/63635471/88565663-91c93600-d052-11ea-94a2-68bdc050ee3c.PNG)

![4](https://user-images.githubusercontent.com/63635471/88565664-9261cc80-d052-11ea-9703-dccde7184307.PNG)


## 2. Define the Sessionized UDF. Sessionize the Clickstream
Open the file sessions.pig and save the following commands:

![scriptfile-1](https://user-images.githubusercontent.com/63635471/88565698-9988da80-d052-11ea-8584-9f7c3bdcbdcb.PNG)

![5](https://user-images.githubusercontent.com/63635471/88565668-92fa6300-d052-11ea-869e-f7a6a88a6ef9.PNG)

![6](https://user-images.githubusercontent.com/63635471/88565671-9392f980-d052-11ea-8ef7-58db648496a7.PNG)


## 3. Compute the Session Length

![scriptfile-2](https://user-images.githubusercontent.com/63635471/88565699-9aba0780-d052-11ea-9e38-8b9462be6622.PNG)

![7](https://user-images.githubusercontent.com/63635471/88565675-942b9000-d052-11ea-8672-afd6b4663170.PNG)

![8](https://user-images.githubusercontent.com/63635471/88565680-955cbd00-d052-11ea-9c5a-68b085e0cf22.PNG)


## 4. Compute the Average Session Length

![scriptfile-3](https://user-images.githubusercontent.com/63635471/88565707-9beb3480-d052-11ea-9066-d5276522281b.PNG)

![9](https://user-images.githubusercontent.com/63635471/88565683-968dea00-d052-11ea-8fa7-5f53a7cc69f9.PNG)

![10](https://user-images.githubusercontent.com/63635471/88565685-97268080-d052-11ea-924a-d5592d80cbf3.PNG)


## 5. Compute the Median Session Length

DEFINE Median datafu.pig.stats.Median();

sessiontimes_avg = FOREACH sessiontimes_all {
ordered = ORDER session_times BY session_length;
GENERATE
AVG(ordered.session_length) AS avg_session,
Median(ordered.session_length) AS median_session;
};

![11](https://user-images.githubusercontent.com/63635471/88565690-9857ad80-d052-11ea-81a6-3ba230cc8378.PNG)

![12](https://user-images.githubusercontent.com/63635471/88565697-98f04400-d052-11ea-926f-c494d5ddf218.PNG)

