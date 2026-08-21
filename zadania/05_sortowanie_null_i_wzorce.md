# Zadanie 1
```sql
select * from course.orders
order by total_amount asc;
```
# Zadanie 2
```sql
select * from course.orders
order by total_amount desc;
```
# Zadanie 3
```sql
select * from course.orders
order by total_amount desc
limit 5;
```
# Zadanie 4
```sql
select * from course.products
order by base_price desc;
```
# Zadanie 5
```sql
select * from course.customers where country in ('PL','DE','FR');
```
# Zadanie 6
```sql
select * from course.orders where total_amount between 100 and 200;
```
# Zadanie 7
```sql
select * from course.customers where email LIKE '%.com';
```
# Zadanie 8
```sql
select * from course.products where product_name like '%Course';
```
# Zadanie 9
```sql
select * from course.customers where email is null;
```
# Zadanie 10
```sql
select * from course.customers where email is not null;
```
# Zadanie 11
```sql
select * from course.customers 
where email is not null 
and country = 'PL';
```
# Zadanie 12
```sql
select * from course.orders
where status = 'paid'
order by total_amount desc;
```
