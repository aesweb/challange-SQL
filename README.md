## Homework : 1

#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql 
SELECT title , description FROM film;
~~~

#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql  
SELECT * FROM film WHERE length >= 60 and length <= 75 ;
~~~

#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql 
SELECT * FROM film WHERE rental_rate = 0.99 and replacement_cost = 12.99 or rental_rate = 0.99 and replacement_cost = 28.99 ; 
~~~

#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql 
SELECT last_name FROM customer WHERE first_name = 'Mary';
~~~

#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql  
SELECT * FROM film WHERE length < 50 and NOT (rental_rate = 2.99 or rental_rate = 4.99)
~~~

## Homework : 2

#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 and 16.99;
~~~

#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name , last_name FROM actor WHERE first_name  IN ('Penelope', 'Nick', 'Ed');
~~~

#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
~~~sql 
SELECT * FROM film WHERE rental_rate  IN (0.99, 2.99, 4.99) and replacement_cost IN (12.99, 15.99, 28.99);
~~~

## Homework : 3

#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql 
SELECT country FROM country WHERE country ~~ 'A%a' ;
~~~

#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql 
SELECT country From Country WHERE LENGTH(country) >= 6 AND country ~~'%n';
~~~

#### Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
~~~sql 
SELECT title FROM film WHERE title ~~* '%t%t%t%t%';
~~~

#### Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql 
SELECT * FROM film WHERE title ~~ 'C%' and length > 90 and rental_rate = 2.99 ;
~~~

## Homework : 4

#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql 
SELECT DISTINCT replacement_cost FROM film ;
~~~

#### Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film ;
~~~

#### Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql 
SELECT COUNT(*) FROM film WHERE title ~~ 'T%' and rating = 'G' ;
~~~

#### Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql 
SELECT COUNT(*) FROM country WHERE country ~~* '_____' ;
~~~

#### City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql 
SELECT COUNT(*) FROM city WHERE city ~~* '%r' ;
~~~

## Homework : 5

#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql 
SELECT * FROM film WHERE title ~~* '%n'  ORDER BY length DESC LIMIT 5;
~~~

#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql 
SELECT * FROM film WHERE title ~~* '%n'  ORDER BY length OFFSET 5 LIMIT 5;
~~~

#### Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql 
SELECT * FROM customer WHERE store_id ='1' ORDER BY last_name DESC LIMIT 4;
~~~

## Homework : 6

#### Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql 
SELECT AVG(rental_rate) FROM film ;
~~~

#### Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql 
SELECT COUNT(*) FROM film WHERE title ~~'C%' ;
~~~

#### Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql 
SELECT MAX(length) FROM film WHERE rental_rate = '0.99' ;
~~~

#### Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length > '150' ;
~~~

## Homework : 7

#### Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql 
SELECT rating FROM film GROUP BY rating ;
~~~

#### Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql 
SELECT replacement_cost,COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) >  50;
~~~

#### Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~sql 
SELECT store_id ,COUNT(*) FROM customer GROUP BY store_id 
~~~

#### City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

~~~sql 
SELECT country_id ,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC 
~~~

## Homework : 8

#### Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql 
CREATE TABLE employee (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
);
~~~

#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
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

#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
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

#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
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

## Homework : 9

#### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql 
SELECT city, country FROM city INNER JOIN country ON city.country_id = country.country_id;
~~~

#### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql 
SELECT payment_id , first_name, last_name FROM customer INNER JOIN payment ON customer.customer_id = payment.customer_id;
~~~

#### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql 
SELECT rental_id , first_name, last_name FROM customer INNER JOIN rental ON customer.customer_id = rental.customer_id;
~~~

## Homework : 10

#### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~sql 
SELECT city, country FROM city LEFT JOIN country ON city.country_id = country.country_id;
~~~

#### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
~~~sql 
SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~

#### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
~~~sql 
SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~

## Homework : 11

#### actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
~~~sql 
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
~~~

#### actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
~~~sql 
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
~~~

#### actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
~~~sql 
(SELECT first_name FROM actor)
EXCEPT 
(SELECT first_name FROM customer);
~~~

#### İlk 3 sorguyu tekrar eden veriler için de yapalım.
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

## Homework : 12

#### Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
~~~sql 
SELECT COUNT(*) as NUMBEROFMOVİES FROM film WHERE length > ANY (SELECT ROUND(AVG(length)) FROM film)
~~~

#### Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
~~~sql 
SELECT COUNT(*) FROM film WHERE rental_rate = ANY (SELECT MAX(rental_rate) FROM film)
~~~

#### Film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
~~~sql 
SELECT DISTINCT title FROM film WHERE rental_rate = any (SELECT MIN(rental_rate) FROM film) AND replacement_cost = any (SELECT MIN(replacement_cost) FROM film)
~~~

#### Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
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









