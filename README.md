# Patika.Dev PostgreSql
[ÖDEV 1](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-1)<br/>
[ÖDEV 2](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-2)<br/>
[ÖDEV 3](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-3)<br/>
[ÖDEV 4](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-4)<br/>
[ÖDEV 5](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-5)<br/>
[ÖDEV 6](https://github.com/civanagi/sqlOdevleri/main/README.md#%C3%B6dev-6)<br/>
## 1. Ödev

### 1 
```sql
SELECT title, description FROM film; 
```
### 2 
```sql 
   SELECT * FROM film
   WHERE length > 60 AND length < 75;
 ```

### 3 
```sql
   SELECT * FROM film
   WHERE rental_rate= 0.99 AND replacement_cost= 12.99 OR replacement_cost= 28.99; 
```

### 4 
```sql 
   SELECT first_name, last_name FROM customer
   WHERE first_name= 'Mary'; 
```
   CEVAP: Smith
     
### 5 
```sql
   SELECT length, rental_rate FROM film
   WHERE NOT length > 50 AND NOT (rental_rate=2.99 OR rental_rate=4.99 );
```

## 2. Ödev

### 1
```sql
select * from film
where replacement_cost between 12.99 and 16.99;
```

### 2
```sql
select first_name, last_name from actor
where first_name in ('Penelope','Nick','Ed') ;
```

### 3
```sql
select * from film
where (rental_rate in (0.99,2.99,4.99)) and (replacement_cost in (12.99, 15.99 , 28.99) ) ;
```

## 3. Ödev

### 1 
```sql
select * from country
where country like 'A%a' ;
```
### 2 
```sql
select country from country
WHERE length(country)>=6 AND country like'%n';
```
### 3
```sql
select * from film
where title ilike '%t%t%t%t%'
```
### 4 
```sql
select * from film
where title like 'C%' and length>90 and rental_rate=2.99 ;
```

## 4. Ödev

### 1
```sql
select distinct replacement_cost from film ;
```
### 2 
```sql
select count(distinct replacement_cost) from film ;
```
### 3
```sql
select count(*) from film 
where title like 'T%' and rating = 'G';
```
### 4 
```sql
select count(*) from country 
where country like '_____'; 
```
### 5 
```sql
select count(*) from city 
where city ilike '%r';
```

## 5. Ödev

### 1
```sql
select * from film
where title like '%n'
order by length desc
limit 5 ;
```
### 2 
```sql
select * from film
where title like '%n'
order by length 
offset 5
limit 5 ;
```
### 3
```sql
select * from customer
where store_id=1
order by last_name desc
limit 4;
```
## 6. Ödev

### 1
```sql
select avg(rental_rate) from film ;
```
### 2 
```sql
SELECT COUNT(*) FROM film 
WHERE title LIKE 'D%' ;
```
### 3
```sql
SELECT max(length) FROM film 
WHERE rental_rate=2.99 ;
```
### 4 
```sql
SELECT count( distinct(replacement_cost)) FROM film 
WHERE length>150 ;
```
