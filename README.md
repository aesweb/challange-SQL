# The challange I solved at the time to apply what I learned, maybe it will help you too

## 1

#### Sort the data in the title and description columns in the movie table.
~~~sql 
SELECT title , description FROM film;
~~~

#### Sort the data in all columns in the movie table with the condition that the movie length is greater than 60 AND less than 75.
~~~sql  
SELECT * FROM film WHERE length >= 60 and length <= 75 ;
~~~

#### Sort the data in all columns in the movie table with the conditions rental_rate 0.99 AND replacement_cost 12.99 OR 28.99.
~~~sql 
SELECT * FROM film WHERE rental_rate = 0.99 and replacement_cost = 12.99 or rental_rate = 0.99 and replacement_cost = 28.99 ; 
~~~

#### What is the value in the last_name column of the customer whose value in the first_name column in the Customer table is 'Mary'?
~~~sql 
SELECT last_name FROM customer WHERE first_name = 'Mary';
~~~

#### Sort the data in the movie table that does NOT have a length greater than 50 and does NOT have a rental_rate of 2.99 or 4.99.
~~~sql  
SELECT * FROM film WHERE length < 50 and NOT (rental_rate = 2.99 or rental_rate = 4.99)
~~~

## 2

#### Sort the data in all columns in the movie table, provided that the replacement cost value is greater than 12.99 and less than 16.99 (use the BETWEEN - AND structure).
~~~sql
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 and 16.99;
~~~

#### Sort the data in the first_name and last_name columns in the Actor table, provided that first_name is 'Penelope' or 'Nick' or 'Ed' (use the IN operator).
~~~sql
SELECT first_name , last_name FROM actor WHERE first_name  IN ('Penelope', 'Nick', 'Ed');
~~~

#### Sort the data in all columns in the movie table with the conditions rental_rate 0.99, 2.99, 4.99 AND replacement_cost 12.99, 15.99, 28.99 (use IN operator).
~~~sql 
SELECT * FROM film WHERE rental_rate  IN (0.99, 2.99, 4.99) and replacement_cost IN (12.99, 15.99, 28.99);
~~~

## 3

#### List the country names in the country column of the country table starting with the character 'A' and ending with the character 'a'.
~~~sql 
SELECT country FROM country WHERE country ~~ 'A%a' ;
~~~

#### List the country names in the country column of the country table that have at least 6 characters and end with the character 'n'.
~~~sql 
SELECT country From Country WHERE LENGTH(country) >= 6 AND country ~~'%n';
~~~

#### At least 4 movie titles in the title column of the movie table containing at least 4 uppercase or lowercase 'T' characters
~~~sql 
SELECT title FROM film WHERE title ~~* '%t%t%t%t%';
~~~

#### Sort the data in all columns in the movie table starting with title 'C', length greater than 90 and rental_rate 2.99.
~~~sql 
SELECT * FROM film WHERE title ~~ 'C%' and length > 90 and rental_rate = 2.99 ;
~~~

## 4

#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql 
SELECT DISTINCT replacement_cost FROM film ;
~~~

#### How many different data are in the replacement_cost column in the movie table?
~~~sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film ;
~~~

#### How many of the movie titles in the movie table start with the character T and also have a rating equal to 'G'?
~~~sql 
SELECT COUNT(*) FROM film WHERE title ~~ 'T%' and rating = 'G' ;
~~~

#### How many of the country names in the Country table have 5 characters?
~~~sql 
SELECT COUNT(*) FROM country WHERE country ~~* '_____' ;
~~~

#### How many of the city names in the City table end with the character 'R' or r?
~~~sql 
SELECT COUNT(*) FROM city WHERE city ~~* '%r' ;
~~~

## 5

#### List the 5 longest movies in the movie table whose title ends with the character 'n'.
~~~sql 
SELECT * FROM film WHERE title ~~* '%n'  ORDER BY length DESC LIMIT 5;
~~~

#### List the second 5 shortest (length) movies in the movie table whose title ends with the character 'n'.
~~~sql 
SELECT * FROM film WHERE title ~~* '%n'  ORDER BY length OFFSET 5 LIMIT 5;
~~~

#### Sort the first 4 data in descending order according to the last_name column in the Customer table, provided that store_id is 1.
~~~sql 
SELECT * FROM customer WHERE store_id ='1' ORDER BY last_name DESC LIMIT 4;
~~~

## 6

#### What is the average of the values in the rental_rate column in the movie table?
~~~sql 
SELECT AVG(rental_rate) FROM film ;
~~~

#### How many of the movies in the movie table start with the character 'C'?
~~~sql 
SELECT COUNT(*) FROM film WHERE title ~~'C%' ;
~~~

#### How many minutes is the longest movie in the movie table with a rental_rate equal to 0.99?
~~~sql 
SELECT MAX(length) FROM film WHERE rental_rate = '0.99' ;
~~~

#### How many different replacement_cost values are in the movie table for movies with a length greater than 150 minutes?
~~~sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length > '150' ;
~~~

## 7

#### Group the movies in the movie table according to their rating values.
~~~sql 
SELECT rating FROM film GROUP BY rating ;
~~~

#### When we group the movies in the movie table according to the replacement_cost column, sort the replacement_cost value with more than 50 movies and the corresponding number of movies.
~~~sql 
SELECT replacement_cost,COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) >  50;
~~~

#### What are the number of customers corresponding to the store_id values in the Customer table?
~~~sql 
SELECT store_id ,COUNT(*) FROM customer GROUP BY store_id 
~~~

#### After grouping the city data in the City table according to the country_id column, share the country_id information and the number of cities with the highest number of cities.

~~~sql 
SELECT country_id ,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC 
~~~

## 8

#### In your test database, let's create a table named employee with column information id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100).
~~~sql 
CREATE TABLE employee (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
);
~~~

#### Let's add 50 data to the employee table we created using the 'Mockaroo' service.
~~~sql 
insert into employee (name, email, birthday) values ('Mack', 'mcartledge0@google.co.uk', '2008-07-22');
insert into employee (name, email, birthday) values ('Fredric', 'fweich1@com.com', null);
insert into employee (name, email, birthday) values ('Lanny', 'lklosser2@hc360.com', '2014-01-31');
insert into employee (name, email, birthday) values ('Gwenneth', 'gchesher3@jiathis.com', '2016-05-28');
insert into employee (name, email, birthday) values ('Lee', 'lgascone4@bloglovin.com', '2002-02-22');
insert into employee (name, email, birthday) values ('Wilton', 'wperello5@vimeo.com', '2003-05-27');
insert into employee (name, email, birthday) values ('Lusa', 'lmurden6@princeton.edu', '2019-09-27');
insert into employee (name, email, birthday) values ('Nariko', 'neakle7@bbc.co.uk', '2015-03-14');
insert into employee (name, email, birthday) values ('Tristan', 'tkrolik8@google.com.hk', '2015-07-27');
insert into employee (name, email, birthday) values ('Stephana', 'sjaukovic9@google.fr', '2015-01-08');
insert into employee (name, email, birthday) values ('Trever', 'tfaroa@1und1.de', '2006-05-18');
insert into employee (name, email, birthday) values ('Analise', null, '2016-10-23');
insert into employee (name, email, birthday) values ('Salim', 'swarrilowc@apache.org', '2001-11-28');
insert into employee (name, email, birthday) values ('Daryn', 'dcordinglyd@cbslocal.com', '2020-05-12');
insert into employee (name, email, birthday) values ('Irene', 'isherrye@miitbeian.gov.cn', null);
insert into employee (name, email, birthday) values ('Ethelda', 'eemanulssonf@reuters.com', '2019-09-05');
insert into employee (name, email, birthday) values ('Inglebert', 'ialsobrookg@nifty.com', '2008-02-11');
insert into employee (name, email, birthday) values ('Bradly', 'bkohlerh@networksolutions.com', '2013-06-12');
insert into employee (name, email, birthday) values ('Thurston', 'thandshearti@bigcartel.com', '2018-11-01');
insert into employee (name, email, birthday) values ('Gayelord', 'gpetrelloj@goodreads.com', null);
insert into employee (name, email, birthday) values ('Delaney', 'dedelheitk@answers.com', null);
insert into employee (name, email, birthday) values ('Domeniga', 'dhaselgrovel@jimdo.com', '2014-01-02');
insert into employee (name, email, birthday) values ('Garey', null, '2007-06-07');
insert into employee (name, email, birthday) values ('Jaye', 'jvonhagtn@diigo.com', '2018-07-31');
insert into employee (name, email, birthday) values ('Mort', 'millsleyo@reverbnation.com', null);
insert into employee (name, email, birthday) values ('Kellia', null, null);
insert into employee (name, email, birthday) values ('Edgard', 'epirazziq@smh.com.au', '2009-09-25');
insert into employee (name, email, birthday) values ('Juli', 'jferencr@statcounter.com', '2002-06-21');
insert into employee (name, email, birthday) values ('Ginger', 'gproscheks@amazon.co.uk', '2008-03-19');
insert into employee (name, email, birthday) values ('Morey', null, '2019-08-22');
insert into employee (name, email, birthday) values ('Holli', 'hobraddenu@bigcartel.com', null);
insert into employee (name, email, birthday) values ('Lew', null, '2007-08-21');
insert into employee (name, email, birthday) values ('Corbett', null, '2016-09-19');
insert into employee (name, email, birthday) values ('Egon', 'etredwellx@slideshare.net', '2016-10-04');
insert into employee (name, email, birthday) values ('Tadio', 'tnealeyy@google.cn', '2012-06-03');
insert into employee (name, email, birthday) values ('Shir', 'sleathartz@tiny.cc', '2012-06-03');
insert into employee (name, email, birthday) values ('Chryste', 'clindholm10@smugmug.com', '2007-10-31');
insert into employee (name, email, birthday) values ('Marrilee', 'mkynnd11@webmd.com', null);
insert into employee (name, email, birthday) values ('Greta', 'gvearnals12@hp.com', null);
insert into employee (name, email, birthday) values ('Karrie', 'kclapson13@mysql.com', '2014-10-12');
insert into employee (name, email, birthday) values ('Tanhya', 'timison14@merriam-webster.com', '2012-04-24');
insert into employee (name, email, birthday) values ('Erny', 'elemonby15@tmall.com', '2004-09-08');
insert into employee (name, email, birthday) values ('Cullin', 'cvillaret16@canalblog.com', '2011-07-01');
insert into employee (name, email, birthday) values ('Reynold', 'rmellem17@symantec.com', '2009-09-09');
insert into employee (name, email, birthday) values ('Mikol', 'mjachimiak18@taobao.com', '2005-02-11');
insert into employee (name, email, birthday) values ('Adolphus', null, '2013-06-02');
insert into employee (name, email, birthday) values ('Friederike', null, '2005-07-02');
insert into employee (name, email, birthday) values ('Lindy', 'lpetegrew1b@kickstarter.com', '2002-07-02');
insert into employee (name, email, birthday) values ('Normy', 'ngoathrop1c@shareasale.com', '2010-08-28');
insert into employee (name, email, birthday) values ('Elissa', 'eheninghem1d@engadget.com', null);
~~~

#### Let's do 5 UPDATE operations that will update other columns according to each of the columns.
~~~sql 
UPDATE employee SET name = 'Ciguli', birthday = '24-06-2004' WHERE name = 'Elissa' RETURNING * ;
~~~
~~~sql 
UPDATE employee SET  email = 'adana01@gmail.com' WHERE name = 'Ciguli' RETURNING * ;
~~~
~~~sql 
UPDATE employee SET  email = 'adana01@gmail.com' WHERE name = 'Mack' RETURNING * ;
~~~
~~~sql 
UPDATE employee SET  birthday = '24-06-2004' WHERE name = 'Mack' RETURNING * ;
~~~
~~~sql 
UPDATE employee SET name = 'Ecrin', email = 'ecnebiecrin@gmail.com', birthday = '24-06-2004' WHERE name = 'Mack' RETURNING * ;
~~~

#### Let's do 5 DELETE operations that will delete the corresponding row according to each of the columns.
~~~sql 
DELETE FROM employee WHERE name = 'Fredric';
~~~
~~~sql 
DELETE FROM employee WHERE id = 8;
~~~
~~~sql 
DELETE FROM employee WHERE birthday = '2014-01-31';
~~~
~~~sql 
DELETE FROM employee WHERE email = 'sjaukovic9@google.fr';
~~~
~~~sql 
DELETE FROM employee WHERE name = 'F%';
~~~

## 9

#### Write the INNER JOIN query that we can see the city and country names in the city table and country table together.
~~~sql 
SELECT city, country FROM city INNER JOIN country ON city.country_id = country.country_id;
~~~

#### Write the INNER JOIN query in which we can see the payment_id in the customer table and payment table and the first_name and last_name names in the customer table together.
~~~sql 
SELECT payment_id , first_name, last_name FROM customer INNER JOIN payment ON customer.customer_id = payment.customer_id;
~~~

#### Write the INNER JOIN query in which we can see the first_name and last_name names in the customer table together with the rental_id in the customer table and rental table.
~~~sql 
SELECT rental_id , first_name, last_name FROM customer INNER JOIN rental ON customer.customer_id = rental.customer_id;
~~~

## 10

#### Write the LEFT JOIN query that we can see the city and country names in the city table and country table together.
~~~sql 
SELECT city, country FROM city LEFT JOIN country ON city.country_id = country.country_id;
~~~

#### Write the RIGHT JOIN query where we can see the payment_id in the customer table and payment table and the first_name and last_name names in the customer table together.
~~~sql 
SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~

#### Write the FULL JOIN query in which we can see the first_name and last_name names in the customer table together with the rental_id in the customer table and rental table.
~~~sql 
SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~

## 11

#### Let's sort all data for first_name columns in actor and customer tables.
~~~sql 
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
~~~

#### Let's sort the intersecting data for first_name columns in actor and customer tables.
~~~sql 
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
~~~

#### For the first_name columns in the actor and customer tables, let's sort the data in the first table but not in the second table.
~~~sql 
(SELECT first_name FROM actor)
EXCEPT 
(SELECT first_name FROM customer);
~~~

#### Let's do the first 3 queries for repeated data.
~~~sql 
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
~~~
~~~sql 
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);
~~~
~~~sql 
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
~~~

## 12

#### In the movie table, the movie length is shown in the length column. How many movies are longer than the average movie length?
~~~sql 
SELECT COUNT(*) as NUMBEROFMOVİES FROM film WHERE length > ANY (SELECT ROUND(AVG(length)) FROM film)
~~~

#### How many movies have the highest rental_rate in the movie table?
~~~sql 
SELECT COUNT(*) FROM film WHERE rental_rate = ANY (SELECT MAX(rental_rate) FROM film)
~~~

#### In the movie table, list the movies with the lowest rental_rate and the lowest replacement_cost.
~~~sql 
SELECT DISTINCT title FROM film WHERE rental_rate = any (SELECT MIN(rental_rate) FROM film) AND replacement_cost = any (SELECT MIN(replacement_cost) FROM film)
~~~

#### List the customers with the highest number of purchases in the Payment table.
##### Condition = 1
~~~sql 
SELECT first_name,last_name
FROM customer c
JOIN payment p
ON ( p.customer_id = c.customer_id )
WHERE amount = ( SELECT MAX(amount) from payment );
~~~

##### Condition = 2
~~~sql 
SELECT first_name, last_name
FROM customer
WHERE customer_id = any
(
SELECT customer_id
FROM payment
WHERE amount = ( SELECT MAX(amount) from payment )
)
~~~









