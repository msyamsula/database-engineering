# database-engineering

REQUIREMENT:
1. relational database (postgres, mysql, oracle, sql-server)

WHAT IS DATABASE ENGINEERING & DESIGN
1. database engineering is an art to create quality database, based on certain principle, and create the model.
2. the result of this engineering is to create fast CRUD and normalize
3. normalize database is a state in database that fully use relational and constraint efficiently
4. there is 3 step to normalize a database
    1st normalization
    a. add field that represent row in each table (usually id)
    b. state that field as primary key
    2nd normalization
    a. pay attention, every column in the table must uniquely define by primary key, if not, create new entity
    b. look at the relation of each entity, should it one-one, one-many, many-many. make use of foreign key to connect them
    3rd normalization
    a. see repeated collumn across all table, you might want to create new entity, if that column happen frequently in your design
5. keep in mind: database is NOT only for keeping your data, it also help us to track of what's happening with our data
6. keep in mind about essential purpose of your database, since it is a limited resource. We may omit certain data if we clear about our database purpose and not store all data
7. gathering requirements means you work with what need to be be improve/done for your database, there is 2 main source in this step which are people and existing system
8. it also nice if you can predict and accumulate data growth in your database. So, you can plan data type and relation accordingly


DATABASE INDEX
1. index is data structure that is created to speed up query in database
2. index is different compare to database
3. the analogy of database index is "address book" in librarian desk
    the "address book" doesn't contain any book but it contains information of fast retrieval of any book in library.
    creating "address book" need more space/memory, in this case more paper, based on how much data we are actually store (the more book in library the longer "address book" will be)
4. index doesn't always mean fast retrieval.. for example if index list listed by book title in alphabetical order. it will not very usefull for retrieving book based on published year. there is needed engineering to create index
5. you can create composite index based on certain parameter. it usually solve querying data that has "and" logical statement
6. in database you can include any field to be stored alongside the index
7. usually index in database use balance-tree data structure
8. to understand how usefull your index. try to "explain analyze" your db query
9. the best possible run for database for fastest to slowest are:
    1. index scan only, we never go into database, index already solve our query
    2. index scan, we use index for searching but, need to go to db for retrieval
    3. index scan with hash, use index but there are lot of data to be retrieve
    4. sequential scan, directly go to database

DATABASE SHARDING
1. in a nutshell, database sharding is to split your table into multiple table in multiple server
2. challenges that arise with database sharding is
    a. consistency: you have to maintain data consistency across server
3. the split is usually based on primary key
3. and, to get what server should i interact with, use hashing function (consistent)