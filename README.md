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
