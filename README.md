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
SELECT * FROM film WHERE length < 50 and NOT rental_rate = 2.99 or length < 50 and NOT rental_rate = 4.99;
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













