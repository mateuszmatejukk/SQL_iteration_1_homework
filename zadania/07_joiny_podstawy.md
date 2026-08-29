## Zadanie 10
```sql
select
c.customer_name,
o.order_id,
p.product_name,
oi.quantity,
oi.unit_price
from course.orders o
inner join course.customers c
on o.customer_id = c.customer_id 
inner join course.order_items oi
on o.order_id = oi.order_id 
inner join course.products p
on oi.product_id = p.product_id;
```
## Zadanie 11
```sql
select
o.order_id,
o.order_date,
c.customer_name,
o.status,
o.total_amount
from course.orders o
join course.customers c
on o.customer_id = c.customer_id
where status = 'paid';
```
## Zadanie 12
```sql
select 
c.customer_id,
c.customer_name,
c.country,
o.status,
o.total_amount
from course.customers c
join course.orders o
on c.customer_id = o.customer_id
where country = 'PL';
```
## Zadanie 13
```sql
select
c.customer_name,
o.order_id,
o.order_date,
o.total_amount
from course.customers c 
join course.orders o
on c.customer_id = o.customer_id 
order by c.customer_name,
o.order_date desc;
```
## Zadanie 14
```sql
select 
c.customer_id,
c.customer_name,
c.country
from course.customers c
left join course.orders o
on c.customer_id = o.customer_id
where o.order_id is null;
```
## Zadanie 15
```sql
select 
p.product_id,
p.product_name,
p.category
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id
where order_id is null;
```
## Zadanie 16
```sql
select distinct
c.country
from course.customers c
join course.orders o
on c.customer_id = o.customer_id
where o.order_id >=1;
```
## Zadanie 17
```sql
select 
c.customer_id,	
c.customer_name,
count(o.order_id) as orders_count
from course.customers c
left join course.orders o
on c.customer_id = o.customer_id
group by c.customer_id;
```
## Zadanie 18
```sql
select
c.customer_id,
c.customer_name,
sum(o.total_amount) as total_revenue
from course.customers c 
left join course.orders o
on c.customer_id = o.customer_id
group by c.customer_id;
```
## Zadanie 19
```sql
select 
oi.product_id,
p.product_name,
sum(oi.quantity) as units_sold
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id
group by oi.product_id, p.product_name;
```
## Zadanie 20
```sql
select 
c.customer_id,
c.customer_name,
count(order_id) as orders_count
from course.customers c 
join course.orders o
on c.customer_id = o.customer_id
group by c.customer_id, c.customer_name
having count(order_id) > 1;
```
## Zadanie 21
```sql
select 
oi.product_id,
p.product_name,
sum(oi.quantity) as units_sold
from course.products p
join course.order_items oi
on p.product_id = oi.product_id
group by oi.product_id, p.product_name 
having sum(oi.quantity) > 1;
```
## Zadanie 22
