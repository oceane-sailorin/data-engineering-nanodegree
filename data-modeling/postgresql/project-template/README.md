# Data Modeling with Postgresql

### Data at our disposal: 

* subset of Million Song Dataset with each file as a json file
    
* log json files based on first dataset
    
Using the datasets, we need to create a database and some tables which column names are extracted from the json files 

### Database:
To create the database, we have several constraints: the columns of each table are given and the pipeline python file is prepared in a certain way with a defined order which prevents from creating the tables with the natural foreign keys and from cleaning the data.




* table users - users in the app
       user_id integer primary key,
       first_name varchar not null,
       last_name varchar not null,
       gender char(1),
       level varchar
       
* songs - songs in music database
       song_id varchar primary key,
       title varchar not null,
       artist_id varchar not null ,
       year integer 
       duration decimal not null
       
* artists - artists in music database
       artist_id varchar primary key,
       name varchar not null,
       location varchar,
       latitude decimal,
       longitude decimal
       
* time - timestamps of records in songplays broken down into specific units
        start_time timestamp primary key,
        hour integer not null 
        day integer not null 
        week integer not null 
        month integer not null 
        year integer not null 
        weekday varchar not null


* songplays - records in log data associated with song plays i.e. records with page NextSong
        songplay_id serial primary key,
        start_time timestamp not null references time(start_time),
        user_id integer references users(user_id),
        level varchar,
        song_id varchar references songs(song_id),
        artist_id varchar references artists(artist_id),
        session_id integer, 
        location varchar,
        user_agent varchar


### Project architecture


* data folder where the json files datasets are
* sql_queries.py contains the queries to create and drop the tables
* create_tables.py contains the python functions to execute the create and the drop of the tables
* test.ipynb to test if the creation of the tables and the insertions in the tables
* etl.ipynb contains the processes to insert data from the datasets in the tables
* etl.py contains the imports, functions and execution of the processes developped first in the etl.ipynb file
* README.md contains some explanations about the project


### Project steps


* Write CREATE statements in sql_queries.py to create each table.
Write the create tables queries according to the instructions and affect them to variables
* Write DROP statements in sql_queries.py to drop each table if it exists.
* Run create_tables.py to create your database and tables.
>> python3 create_tables.py
* Run test.ipynb to confirm the creation of your tables with the correct columns. Make sure to click "Restart kernel" to close the connection to the database after running this notebook.

#### Build ETL Processes

* Follow instructions in the etl.ipynb notebook to develop ETL processes for each table. At the end of each table section, or at the end of the notebook, run test.ipynb to confirm that records were successfully inserted into each table. Remember to rerun create_tables.py to reset your tables before each time you run this notebook.
Use python code to connect to database, read json files, extract data, format data and insert into create tables.
Check if insertions done properly

* Use what you've completed in etl.ipynb to complete etl.py, where you'll process the entire datasets. Remember to run create_tables.py before running etl.py to reset your tables. Run test.ipynb to confirm your records were successfully inserted into each table.
Copy what was developed in etl.ipynb to etl.py





