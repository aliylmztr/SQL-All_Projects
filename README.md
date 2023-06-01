# SQL-All_Projects
All my assignments in SQL programming language

www.patika.dev

----------------------------------------------

--------------- SQL-Odev1 | SELECT | WHERE | Karşılaştırma ve Mantıksal Operatörler ---------------

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

SELECT title, description FROM film;

2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

SELECT * FROM film
WHERE length > 60 AND length < 75;

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;

4. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

SELECT * FROM film
WHERE length <= 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);

----------------------------------------------

" SQL-Odev2 | BETWEEN ve IN "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan tüm sütunlardaki verileri replacement_cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;

2. actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);

----------------------------------------------

" SQL-Odev3 | LIKE ve ILIKE "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

SELECT country FROM country
WHERE country LIKE 'A%a';

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

SELECT country FROM country
WHERE country LIKE '_____%n';

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

SELECT title FROM film
WHERE title ILIKE '%T%T%T%T%';

4. film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;

----------------------------------------------

" SQL-Odev4 | DISTINCT ve COUNT "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

SELECT DISTINCT replacement_cost FROM film;

2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

SELECT COUNT(DISTINCT replacement_cost) FROM film;

3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';

4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

SELECT COUNT(*) FROM country
WHERE country LIKE '_____';

5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya 'r' karakteri ile biter?

SELECT COUNT(*) FROM city
WHERE city ILIKE '%R';

----------------------------------------------

" SQL-Odev5 | ORDER BY | LIMIT ve OFFSET "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

SELECT * FROM film
WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5;

2. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

SELECT * FROM film
WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;

3. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

SELECT * FROM customer
WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;

----------------------------------------------

" SQL-Odev6 | Aggregate Fonksiyonlar "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

SELECT AVG(rental_rate) FROM film;

2. film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';

3. film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;

4. film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;

----------------------------------------------

" SQL-Odev7 | GROUP BY | HAVING "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

SELECT rating, COUNT(*) FROM film GROUP BY rating;

2. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost HAVING COUNT(*) > 50;

3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayıları nelerdir?

SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;

4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

SELECT country_id, COUNT(*) FROM city
GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;

----------------------------------------------

" SQL-Odev8 | CREATE | DROP | INSERT INTO | UPDATE & SET | DELETE "

1. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
);

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

insert into employee (id, name, birthday, email) values (1, 'Rosemary', '2021-01-16', 'rhofton0@gmpg.org');
insert into employee (id, name, birthday, email) values (2, 'Eolande', '1941-10-31', 'ecamus1@ucoz.ru');
insert into employee (id, name, birthday, email) values (3, 'Constantin', '1934-05-06', 'camyes2@storify.com');
insert into employee (id, name, birthday, email) values (4, 'Monti', '1998-01-18', 'mstonuary3@blinklist.com');
insert into employee (id, name, birthday, email) values (5, 'Akim', '1962-11-12', 'agribbin4@csmonitor.com');
insert into employee (id, name, birthday, email) values (6, 'Trev', null, 'tdomnick5@skyrock.com');
insert into employee (id, name, birthday, email) values (7, 'Eddie', null, 'erosbotham6@newyorker.com');
insert into employee (id, name, birthday, email) values (8, 'Augusta', null, 'averry7@phpbb.com');
insert into employee (id, name, birthday, email) values (9, 'Mollee', null, 'memney8@topsy.com');
insert into employee (id, name, birthday, email) values (10, 'Fanechka', '1958-03-20', 'fringsell9@latimes.com');
insert into employee (id, name, birthday, email) values (11, 'Cheslie', null, 'cletteressea@addtoany.com');
insert into employee (id, name, birthday, email) values (12, 'Torre', '1944-09-08', 'tskehensb@illinois.edu');
insert into employee (id, name, birthday, email) values (13, 'Marjorie', '1935-04-15', 'mvollamc@slideshare.net');
insert into employee (id, name, birthday, email) values (14, 'Jonathan', '1992-09-10', null);
insert into employee (id, name, birthday, email) values (15, 'Wendall', '1942-03-09', 'wgrimwade@independent.co.uk');
insert into employee (id, name, birthday, email) values (16, 'Selinda', '2019-09-10', 'sollertonf@moonfruit.com');
insert into employee (id, name, birthday, email) values (17, 'Artemus', '1961-08-11', 'anucciig@free.fr');
insert into employee (id, name, birthday, email) values (18, 'Enrico', null, 'evaterh@examiner.com');
insert into employee (id, name, birthday, email) values (19, 'Deane', null, 'dhaironi@goo.gl');
insert into employee (id, name, birthday, email) values (20, 'Carce', '1953-01-14', 'cleaknerj@youtube.com');
insert into employee (id, name, birthday, email) values (21, 'Annora', '1960-05-16', 'agwynnk@harvard.edu');
insert into employee (id, name, birthday, email) values (22, 'Caryl', '1958-07-03', 'cdimontl@webnode.com');
insert into employee (id, name, birthday, email) values (23, 'Garwin', '1943-03-24', 'gfakem@ucsd.edu');
insert into employee (id, name, birthday, email) values (24, 'Laraine', '1970-04-04', 'lbalchenn@xing.com');
insert into employee (id, name, birthday, email) values (25, 'Clara', '1983-07-07', 'cmcgenniso@indiatimes.com');
insert into employee (id, name, birthday, email) values (26, 'Aurelie', '1934-10-08', 'acockroftp@csmonitor.com');
insert into employee (id, name, birthday, email) values (27, 'George', '2023-02-18', 'gpoleq@va.gov');
insert into employee (id, name, birthday, email) values (28, 'Harriett', null, 'hhummerstonr@cbslocal.com');
insert into employee (id, name, birthday, email) values (29, 'Tiffi', '1980-07-31', 'tstammlers@sourceforge.net');
insert into employee (id, name, birthday, email) values (30, 'Joelly', '1962-10-24', 'jgussint@princeton.edu');
insert into employee (id, name, birthday, email) values (31, 'Trace', '1946-09-16', 'ttriggelu@blog.com');
insert into employee (id, name, birthday, email) values (32, 'Emmaline', '1978-01-22', 'elanbertoniv@skyrock.com');
insert into employee (id, name, birthday, email) values (33, 'Monica', '1926-01-11', 'mchatinw@tmall.com');
insert into employee (id, name, birthday, email) values (34, 'Cherrita', '1974-03-11', 'cswettenhamx@earthlink.net');
insert into employee (id, name, birthday, email) values (35, 'Isidor', '2021-06-09', 'iantonichy@mtv.com');
insert into employee (id, name, birthday, email) values (36, 'Sabine', '1995-11-01', 'sledramz@guardian.co.uk');
insert into employee (id, name, birthday, email) values (37, 'Hamlin', '1966-05-01', null);
insert into employee (id, name, birthday, email) values (38, 'Benedicta', '1970-09-25', 'bjales11@issuu.com');
insert into employee (id, name, birthday, email) values (39, 'Rollie', null, 'rmcnelly12@qq.com');
insert into employee (id, name, birthday, email) values (40, 'Candice', '1936-03-28', null);
insert into employee (id, name, birthday, email) values (41, 'Ronica', '1941-12-30', 'rrosina14@hostgator.com');
insert into employee (id, name, birthday, email) values (42, 'Silvan', '1970-12-19', 'sshillingford15@vinaora.com');
insert into employee (id, name, birthday, email) values (43, 'Baxie', '1944-01-23', 'btomasik16@edublogs.org');
insert into employee (id, name, birthday, email) values (44, 'Maureene', '1970-07-02', 'mstenton17@nps.gov');
insert into employee (id, name, birthday, email) values (45, 'Desiree', null, 'dkarpushkin18@dailymotion.com');
insert into employee (id, name, birthday, email) values (46, 'Car', '2012-01-19', 'cbrehaut19@abc.net.au');
insert into employee (id, name, birthday, email) values (47, 'Kakalina', '1928-09-01', 'kanstice1a@aboutads.info');
insert into employee (id, name, birthday, email) values (48, 'Jourdain', '1987-11-02', 'jhawtry1b@indiatimes.com');
insert into employee (id, name, birthday, email) values (49, 'Ciel', '2016-01-07', null);
insert into employee (id, name, birthday, email) values (50, 'Berget', '2021-05-01', 'bwharrier1d@slideshare.net');

3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

// 1

UPDATE employee
SET name = 'Montana',
	birthday = '1999-02-19',
	email = 'montana@blinklist.com'
WHERE id = 4;

// 2

UPDATE employee
SET birthday = '2020-09-10',
	email = 'selinda@moonfruit.com'
WHERE name = 'Selinda';

// 3

UPDATE employee
SET name = 'Clair',
	email = 'clara@indiatimes.com'
WHERE birthday = '1983-07-07';

// 4

UPDATE employee
SET name = 'Tiffani',
	birthday = '1990-08-30'
WHERE email = 'tstammlers@sourceforge.net';

// 5

UPDATE employee
SET name = 'Sabbin',
	birthday = '1996-12-01',
	email = 'sabbin@guardian.com'
WHERE id = 36;

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

// 1

DELETE FROM employee
WHERE id = 10;

// 2

DELETE FROM employee
WHERE name = 'Torre';

// 3

DELETE FROM employee
WHERE birthday ='1970-04-04';

// 4

DELETE FROM employee
WHERE email = 'elanbertoniv@skyrock.com';

// 5

DELETE FROM employee
WHERE id > 20
RETURNING *;

----------------------------------------------

" SQL-Odev9 | INNER JOIN "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id;

2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id;

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
INNER JOIN rental ON customer.customer_id = rental.customer_id;

----------------------------------------------

" SQL-Odev10 | LEFT JOIN | RIGHT JOIN | FULL JOIN "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

SELECT city.city, country.country FROM city
LEFT JOIN country ON city.country_id = country.country_id;

2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
RIGHT JOIN payment ON customer.customer_id = payment.customer_id;

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id;

----------------------------------------------

" SQL-Odev11 | UNION | INTERSECT ve EXCEPT "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);

2. actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);

3. actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);

4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

//1

(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);

//2

(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);

//3

(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);

----------------------------------------------

" SQL-Odev12 | Subquery | ANY | ALL "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

SELECT COUNT(*) FROM film WHERE length >
(
	SELECT AVG(length) FROM film 
);

2. film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

SELECT COUNT(*) FROM film WHERE rental_rate =
(
	SELECT MAX(rental_rate) FROM film
);

3. film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

SELECT * FROM film WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);

4. payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

SELECT customer_id, COUNT(*) FROM payment
GROUP BY customer_id ORDER BY COUNT(*) DESC;

----------------------------------------------

" SQL-Odev13 | An Overview "

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kaç tane film vardır?

SELECT COUNT(*) FROM film WHERE title ILIKE '%E%E%E%E%';

2. category tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.

SELECT COUNT(*), category.name FROM category
JOIN film_category ON film_category.category_id = category.category_id
JOIN film ON film.film_id = film_category.film_id
GROUP BY category.name;

3. film tablosunda en fazla sayıda film bulunduran rating kategorisi hangisidir?

SELECT rating, COUNT(*) FROM film
GROUP BY rating ORDER BY COUNT(*) DESC LIMIT 1;

4. film tablosunda 'K' karakteri ile başlayan en uzun ve replacemet_cost değeri en düşük 4 filmi sıralayınız.

SELECT title, length, replacement_cost FROM film
WHERE title LIKE 'K%' ORDER BY length DESC, replacement_cost ASC LIMIT 4;

5. customer tablosunda alışverişte en çok harcama yapan müşterinin adı nedir?

SELECT SUM(amount), customer.first_name, customer.last_name FROM payment
JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id, customer.first_name, customer.last_name ORDER BY SUM(amount) DESC LIMIT 1;

