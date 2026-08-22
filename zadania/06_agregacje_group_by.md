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
