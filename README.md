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
  
  
