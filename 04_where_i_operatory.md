# Zadanie 1
```sql
select * 
from course.customers
where country = 'PL';
```
# Zadanie 2
```sql
select * 
from course.customers
where country = 'DE';
```
# Zadanie 3
```sql
select * 
from course.orders
where total_amount > 100;
```
# Zadanie 4
```sql
select * 
from course.orders
where total_amount < 100;
```
# Zadanie 5
```sql
select * 
from course.orders
where status = 'paid';
```
# Zadanie 6
```sql
select * 
from course.orders
where status <> 'paid';
```
# Zadanie 7
```sql
select * 
from course.products
where base_price >= 150;
```
# Zadanie 8
```sql
select * 
from course.orders
where status = 'paid' and total_amount > 150;
```
# Zadanie 9
```sql
select * 
from course.customers
where country = 'PL' or country = 'DE';
```
# Zadanie 10
```sql
select * 
from course.orders
where total_amount > 100
and (status = 'paid' or status = 'pending');
```
