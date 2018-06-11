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

Database design starts with a picture....

so in building a data model you often ask, what is the first table? and usually you think about it is like, what is the core purpose of this application? 

Database Normalization:

Dont replicate vertically data.

The rule of what we were trying to do was no vertical duplication of columns that has strings in them. It's okay to have vertical duplication  of columns that have integers.

A foreign key is when a table has a  column containing a key that points to the primary key of another table.



The JOIN Operation:


JOIN says more than one table and the ON clause says the rules upon which we can do this.

Many to one relationship
there could be many albums for one artist.

album_id, title, artist_id     artist_id, name
1 A 2                             1         X
2 B 2                             2         Y

Joining two tables without ON clause gives all possible combinations of rows.
Throw away the non-matching rows is what the ON clause really does.


What we want to see 
The tables that hold the data
How the tablesa are linked.


ON DELETE CASCADE
This is like saying, in this table we are pointing to a row in another table.
We are telling MySql to "clean up" broken references.
we do that to maintain database consistency.

https://stackoverflow.com/questions/1027656/what-is-mysqls-default-on-delete-behavior

we have done everything that's one to many relationships.
and now we are going to do many-to-many relationships, which is kind of the other major way of connecting tables together.

so everything we have done so far is many to one. and that just means that you can have lots of rows that are like seven, seven, seven in the track and then there is seven over here, there is on seven

Many-To-Many Relationships:

problem is that you can have many users and you can have many courses and many users can be a member of many courses and many courses can have many users.

we need to add a "connection" table with two foreign keys

A book can have multiple authors and an author can write multiple books.

we dont have a single primary key. we have a combination promary key or a concatenated primary key and so we just give it two things.


























                                                                                            



  
  
