## Zadanie 1
```sql
select
order_id,
total_amount
from course.orders 
where total_amount > (
select avg(total_amount)
from course.orders
);
```
## Zadanie 2
```sql
select
customer_id,
customer_name
from course.customers 
where customer_id IN(
select customer_id
from course.orders
);
```
## Zadanie 3
```sql
select
customer_id,
customer_name
from course.customers 
where customer_id not in (
select customer_id
from course.orders
);
```
## Zadanie 4
```sql
select
product_id,
product_name
from course.products 
where product_id in (
select product_id
from course.order_items
);
```
## Zadanie 5
```sql
select
order_id,
status,
total_amount
from course.orders 
where total_amount > (
select max(total_amount) 
from course.orders 
where status = 'cancelled'
);
```
## Zadanie 6
```sql
select
customer_id
total_revenue
from (
select
customer_id,
sum(total_amount) as total_revenue
from course.orders 
group by customer_id
)customer_revenue
where total_revenue > 200;
```
## Zadanie 7
```sql
select 
order_id,
total_amount,
(
	select round(avg(total_amount),2)
	from course.orders
 )	as average_order_value
from course.orders;
```
## Zadanie 8
```sql
select
c.customer_id,
c.customer_name
from course.customers c
where exists (
select 1
from course.orders o
where c.customer_id = o.customer_id
);
```
## Zadanie 9
```sql
select
c.customer_id,
c.customer_name
from course.customers c
where not exists (
select 1
from course.orders o
where c.customer_id = o.customer_id
);
```
## Zadanie 10
