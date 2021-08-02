# sqlOdevleri

# 1. Ödev
###1 ```sql
select title, description from film; 
´´´
###2 ```sql 
   select * from film
   where length > 60 and length < 75; ´´´

###3 ```sql
   select * from film
   where rental_rate= 0.99 and replacement_cost= 12.99 or replacement_cost= 28.99; ```

###4 ```sql 
   select first_name, last_name from customer
   where first_name= 'Mary'; ```
   
   Cevap: Smith
   
###5 ```sql
   select length, rental_rate from film
   where not length > 50 and not (rental_rate=2.99 or rental_rate=4.99 ) ```
