# Patika.Dev PostgreSql

## 1. Ödev

### 1 Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

```sql
SELECT title, description FROM film; 
```
### 2 Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

```sql 
   SELECT * FROM film
   WHERE length > 60 AND length < 75;
 ```

### 3 Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

```sql
   SELECT * FROM film
   WHERE rental_rate= 0.99 AND replacement_cost= 12.99 OR replacement_cost= 28.99; 
```

### 4 Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```sql 
   SELECT first_name, last_name FROM customer
   WHERE first_name= 'Mary'; 
```
   CEVAP: Smith
     
### 5 Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```sql
   SELECT length, rental_rate FROM film
   WHERE NOT length > 50 AND NOT (rental_rate=2.99 OR rental_rate=4.99 );
```

## 2. Ödev

### 1 Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız. (BETWEEN - AND yapısını kullanınız.)

```sql
select * from film
where replacement_cost between 12.99 and 16.99;
```

### 2 Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. (IN operatörünü kullanınız.)

```sql
select first_name, last_name from actor
where first_name in ('Penelope','Nick','Ed') ;
```

### 3 Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. (IN operatörünü kullanınız.)

```sql
select * from film
where (rental_rate in (0.99,2.99,4.99)) and (replacement_cost in (12.99, 15.99 , 28.99) ) ;
```

## 3. Ödev

### 1 Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
select * from country
where country like 'A%a' ;
```
### 2 Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```sql
select country from country
WHERE length(country)>=6 AND country like'%n';
```
### 3 Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
select * from film
where title ilike '%t%t%t%t%'
```
### 4 Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```sql
select * from film
where title like 'C%' and length>90 and rental_rate=2.99 ;
```

## 4. Ödev

### 1 Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```sql
select distinct replacement_cost from film ;
```
### 2 Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```sql
select count(distinct replacement_cost) from film ;
```
### 3 Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```sql
select count(*) from film 
where title like 'T%' and rating = 'G';
```
### 4 Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```sql
select count(*) from country 
where country like '_____'; 
```
### 5 City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```sql
select count(*) from city 
where city ilike '%r';
```

## 5. Ödev

### 1 Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```sql
select * from film
where title like '%n'
order by length desc
limit 5 ;
```
### 2 Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

```sql
select * from film
where title like '%n'
order by length 
offset 5
limit 5 ;
```
### 3 Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```sql
select * from customer
where store_id=1
order by last_name desc
limit 4;
```
## 6. Ödev

### 1 Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
select avg(rental_rate) from film ;
```
### 2 Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

```sql
SELECT COUNT(*) FROM film 
WHERE title LIKE 'D%' ;
```
### 3 Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```sql
SELECT max(length) FROM film 
WHERE rental_rate=2.99 ;
```
### 4 Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```sql
SELECT count( distinct(replacement_cost)) FROM film 
WHERE length>150 ;
```

## 7. Ödev

### 1 Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```sql
select rating from film
group by rating ;
```
### 2 Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

```sql
select replacement_cost, count(*) from film
group by replacement_cost
having count(*) > 50;
```
### 3 Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

```sql
select store_id, count(*) from customer
group by store_id ;
```
### 4 City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

```sql
select country_id, count(*) from city
group by country_id
order by count(*) desc
limit 1 ;
```
## 8. Ödev

### 1 test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```sql
create table employee(
	id INTEGER, 
	name Varchar(50) NOT NULL,
	birthday DATE,
	email varchar(100)
);
```
### 2 Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

```sql
insert into employee (id, name, birthday, email) values (1, 'Starr Vincent', '1959/09/14', 'svincent0@barnesandnoble.com');
insert into employee (id, name, birthday, email) values (2, 'Deni Woolaston', '1969/06/15', 'dwoolaston1@amazon.de');
insert into employee (id, name, birthday, email) values (3, 'Billie Roseby', '1988/09/03', 'broseby2@forbes.com');
insert into employee (id, name, birthday, email) values (4, 'Cal Stirgess', '1999/07/12', 'cstirgess3@cdbaby.com');
insert into employee (id, name, birthday, email) values (5, 'Nathalie Fossett', '1969/01/27', 'nfossett4@surveymonkey.com');
insert into employee (id, name, birthday, email) values (6, 'Eduard Drewe', '2000/08/19', 'edrewe5@joomla.org');
insert into employee (id, name, birthday, email) values (7, 'Maddy Jeckell', '1997/05/28', 'mjeckell6@parallels.com');
insert into employee (id, name, birthday, email) values (8, 'Adelice Toopin', '1977/05/06', 'atoopin7@topsy.com');
insert into employee (id, name, birthday, email) values (9, 'Keeley Mounch', '1952/01/17', 'kmounch8@reuters.com');
insert into employee (id, name, birthday, email) values (10, 'Xena Witcomb', '1973/09/15', 'xwitcomb9@auda.org.au');
insert into employee (id, name, birthday, email) values (11, 'Toinette Touret', '1930/10/30', 'ttoureta@hc360.com');
insert into employee (id, name, birthday, email) values (12, 'Geneva McKilroe', '1964/12/21', 'gmckilroeb@tripod.com');
insert into employee (id, name, birthday, email) values (13, 'Brana Kimmings', '1903/06/12', 'bkimmingsc@usatoday.com');
insert into employee (id, name, birthday, email) values (14, 'Rafaello Domegan', '1904/06/01', 'rdomegand@nps.gov');
insert into employee (id, name, birthday, email) values (15, 'Wilmar Ponceford', '1926/03/16', 'wponceforde@about.com');
insert into employee (id, name, birthday, email) values (16, 'Albrecht Mazzia', '1907/01/12', 'amazziaf@reuters.com');
insert into employee (id, name, birthday, email) values (17, 'Raimondo Norville', '2002/02/21', 'rnorvilleg@hostgator.com');
insert into employee (id, name, birthday, email) values (18, 'Wallie Worcester', '1926/09/30', 'wworcesterh@microsoft.com');
insert into employee (id, name, birthday, email) values (19, 'Rudolf Stodhart', '1912/12/06', 'rstodharti@biglobe.ne.jp');
insert into employee (id, name, birthday, email) values (20, 'Sherri Cardero', '2001/02/08', 'scarderoj@sourceforge.net');
insert into employee (id, name, birthday, email) values (21, 'Jannel Tidbury', '1992/08/08', 'jtidburyk@free.fr');
insert into employee (id, name, birthday, email) values (22, 'Udall Sponder', '1957/09/21', 'usponderl@engadget.com');
insert into employee (id, name, birthday, email) values (23, 'Lennie Corton', '1944/10/12', 'lcortonm@odnoklassniki.ru');
insert into employee (id, name, birthday, email) values (24, 'Karol Cotter', '1982/02/25', 'kcottern@businesswire.com');
insert into employee (id, name, birthday, email) values (25, 'Jamaal Shouler', '1941/07/11', 'jshoulero@stanford.edu');
insert into employee (id, name, birthday, email) values (26, 'Salomo Scading', '1961/09/19', 'sscadingp@noaa.gov');
insert into employee (id, name, birthday, email) values (27, 'Lonnie Meates', '1975/01/24', 'lmeatesq@fc2.com');
insert into employee (id, name, birthday, email) values (28, 'Nola Ludlom', '1933/11/11', 'nludlomr@gov.uk');
insert into employee (id, name, birthday, email) values (29, 'Adriane Taysbil', '1925/08/10', 'ataysbils@bloomberg.com');
insert into employee (id, name, birthday, email) values (30, 'Devora Ecclestone', '1942/07/23', 'decclestonet@businesswire.com');
insert into employee (id, name, birthday, email) values (31, 'Milly Drakes', '1918/08/27', 'mdrakesu@usgs.gov');
insert into employee (id, name, birthday, email) values (32, 'Loy Iowarch', '1912/01/19', 'liowarchv@tumblr.com');
insert into employee (id, name, birthday, email) values (33, 'Denna Ilymanov', '1999/09/23', 'dilymanovw@instagram.com');
insert into employee (id, name, birthday, email) values (34, 'Marney Winfred', '1996/06/19', 'mwinfredx@biglobe.ne.jp');
insert into employee (id, name, birthday, email) values (35, 'Lindsy Mayzes', '1967/01/07', 'lmayzesy@loc.gov');
insert into employee (id, name, birthday, email) values (36, 'Berny Ligertwood', '1918/07/05', 'bligertwoodz@friendfeed.com');
insert into employee (id, name, birthday, email) values (37, 'Hunter Pennaman', '1953/05/08', 'hpennaman10@rediff.com');
insert into employee (id, name, birthday, email) values (38, 'Fina Arnull', '1903/09/02', 'farnull11@prlog.org');
insert into employee (id, name, birthday, email) values (39, 'Mimi Voden', '1949/06/24', 'mvoden12@yahoo.co.jp');
insert into employee (id, name, birthday, email) values (40, 'Ciel Millin', '1912/10/16', 'cmillin13@mozilla.org');
insert into employee (id, name, birthday, email) values (41, 'Shelbi Rowell', '1981/10/09', 'srowell14@statcounter.com');
insert into employee (id, name, birthday, email) values (42, 'Gerek Bridgwood', '1978/06/22', 'gbridgwood15@sourceforge.net');
insert into employee (id, name, birthday, email) values (43, 'Cody Saddington', '1925/04/27', 'csaddington16@merriam-webster.com');
insert into employee (id, name, birthday, email) values (44, 'Rozalie Epps', '1957/02/11', 'repps17@foxnews.com');
insert into employee (id, name, birthday, email) values (45, 'Sandie Berk', '1912/08/16', 'sberk18@miitbeian.gov.cn');
insert into employee (id, name, birthday, email) values (46, 'Collete Broomer', '1921/04/29', 'cbroomer19@parallels.com');
insert into employee (id, name, birthday, email) values (47, 'Whit FitzGibbon', '1978/04/02', 'wfitzgibbon1a@eepurl.com');
insert into employee (id, name, birthday, email) values (48, 'Padgett Shayler', '1912/10/03', 'pshayler1b@ifeng.com');
insert into employee (id, name, birthday, email) values (49, 'Janek Marc', '1909/04/13', 'jmarc1c@psu.edu');
insert into employee (id, name, birthday, email) values (50, 'Beatrisa Killelay', '2003/03/05', 'bkillelay1d@discovery.com');
```
### 3 Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```sql
update employee
set name='Tim Cook',
	birthday='1960-11-01',
	email='tim@cook.com'
where id=3;
update employee
set name= 'Thomas Warth',
	birthday= '1961-09-10',
	email='thomas@warth'
where id=4;
```
### 4 Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```sql
delete from employee
where id>48 ;

delete from employee
where id=1;

delete from employee
where name='Starr Vincent';

delete from employee
where birthday='1969-06-15';

delete from employee
where email='gmckilroeb@tripod.com';
```

## 9. Ödev

### 1 city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select city, country from city
inner join country on country.country_id = city.country_id;
```
### 2 customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select payment_id , first_name, last_name from customer
inner join payment on customer.customer_id = payment.customer_id;
```
### 3 customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select rental_id, first_name, last_name from customer
inner join rental on rental.customer_id = customer.customer_id;
```
