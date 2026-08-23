# Zadanie 1
```sql
select count(*) as quantity_of_customers
from course.customers;
```
# Zadanie 2
```sql
select count(*) as quantity_of_products
from course.products;
```
# Zadanie 3
```sql
select count(*) as quantity_of_orders
from course.orders;
```
# Zadanie 4
```sql
select sum(total_amount) as sum_of_orders
from course.orders;
```
# Zadanie 5
```sql
select avg(total_amount) as avg_of_orders
from course.orders;
```
# Zadanie 6
```sql
select min(total_amount) as minimum_order
from course.orders;
```
```sql
select max(total_amount) as maximum_order
from course.orders;
```
# Zadanie 7
```sql
select country, count(*) as customers_count from course.customers
group by country
order by customers_count;
```
# Zadanie 8
```sql
select status, count(*) as orders_amount
from course.orders
group by status;
```
# Zadanie 9
```sql
select status,
sum (total_amount) as total_revenue
from course.orders
group by status;
```
# Zadanie 10
```sql
select category,
count (category) as quantity_of_products
from course.products
group by category
order by quantity_of_products desc;
```
# Zadanie 11
```sql
select country, count (*) as customers_count
from course.customers
where email is not null
group by country;
```
# Zadanie 12
```sql
select status, count(*) as orders_count
from course.orders
group by status
having count(*) > 2;
```
# Zadanie 13
```sql
select status, 
avg(total_amount) as average_order_value
from course.orders
group by status
order by average_order_value desc;
```
