# Project: Data-Warehouse-with-AWS
## Introduction
Sparkify has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.<br>
Build an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to. Test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.
## Project Description
Work on data warehouses and AWS to build an ETL pipeline for a database hosted on Redshift. Need to load data from S3 to staging tables on Redshift and execute SQL statements that create the analytics tables from these staging tables.
## Project Datasets
### Song Dataset
Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. <br>
For example,
```
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```
### Log dataset:
It consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.<br>
For example,
```
{"artist": null, "auth": "Logged In", "firstName": "Walter", "gender": "M", "itemInSession": 0, "lastName": "Frye", "length": null, "level": "free", "location": "San Francisco-Oakland-Hayward, CA", "method": "GET","page": "Home", "registration": 1540919166796.0, "sessionId": 38, "song": null, "status": 200, "ts": 1541105830796, "userAgent": "\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"", "userId": "39"}
```
## Schema for Song Play Analysis
A **star schema** is required for optimized queries on song play queries.<br>
![image](https://github.com/MengyaCao/Data-Warehouse-with-AWS/blob/main/ER_Diagram_DW.JPG)<br>
> **Fact Table**<br>
>> * **songplays** - records in event data associated with song plays i.e. records with page `NextSong`<br>
```songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent```<br>
> **Dimension Tables**<br>
>> * **users** - users in the app<br>
```user_id, first_name, last_name, gender, level```<br>
>> * **songs** - songs in music database<br>
```song_id, title, artist_id, year, duration```<br>
>> * **artists** - artists in music database<br>
```artist_id, name, location, lattitude, longitude```<br>
>> * **time** - timestamps of records in songplays broken down into specific units<br>
```start_time, hour, day, week, month, year, weekday```<br>



