# sql

Thw way we talk to database servers.


Starting mysql in linux:
mysql -u root -p 

Creating a Database:
CREATE DATABASE people DEFAULT CHARACTER SET utf8;
CREATE TABLE users (name VARCHAR(128), email VARCHAR(128));


SHOW databases;
USE people;
DESCRIBE users;


INSERT INTO USERS (name. email) VALUES ('sweta', 'sweta.sharma@test.com');
DELETE FROM users WHERE email='sweta.sharma@test.com'
Think of delete as a loop on table and where as if statement.
UPDATE users SET anme='test' WHERE email='sweta.sharma@test.com'
SELECT * FROM users ORDER BY email
SELECT * FROM users WHERE name LIKE '%e%'
SELECT * FROM Users ORDER BY  email DESC LIMIT 1,2
SELECT count(*) FROM Users -> how many rows ar r there in the user table


DATA TYPES IN SQL:

DATABASE KEYS AND INDEXES:

AUTO_INCREMENT

Often as we make multiple tables and need to JOIN them together we need an integer primary key for each row so we can efficiently add a reference to a row in some other table as a foreign key.

CREATE TABLE users (user_id INT UNSIGNED NOT NULL AUTO_INCREMENT, name VARCHAR(128), email VARCHAR(128), PRIMARY KEY(user_id), INDEX(email))
unsigned meaning positive only, not null means its required, auto_increment please supply it if I dont
Primary key: which means we are going to use it a lot
INDEX: we are going to look up with WHERE clauses using this a lot.

Indexes: If you dont tell it to index something and you select something, it may have to scan the entire table and its likeoh that's going to take a while. if there's hundreds of thousands of records, these things can slow down.

As a table gets large (they always do), scanning all the data to find a single row becomes bery costly.
There are techniques to greatly shorten the scan as long as you create data structure and maintain those structures - like shortcuts.

There's a coupple of differenr kinds of indexes, There's a Hash or Tree.
The hash is used often in primary keys for exact matches and the Trees are used for sorting and prefix matches.

B-Trees are good for sorted kind of material and prefix material, especially like a string.If you are looking up names and and you are looking up names that started with ch. you still could find the right spot and then you would scan for all the Ch's basically.

A B-Tree is a tree data structure that keeps data sorteda and allows searches, sequential access, insertions, and deletions in logarithmic anortized time. The B-tree is optimized for systems that read and write large blocks of data. Is is commonly used in databases and file systems.

idea is there's a small amount of data that points to the higher chunks of data.

Hashes:
keys hash funciton hashes
The values returned by a hash funmction are called hash values, hash codes. hash sums, checksums, or simply hashes
this didnt take any talking to disk drive.

ALTER TABLE Users ADD INDEX ( email );

Relational Database Design:

  
  
