## Zadanie 1
```sql
select 
customer_id,
customer_name,
country,
coalesce(email, 'missing email') as email
from course.customers 
where country = 'PL' or country = 'DE' or country = 'FR';
```
## Zadanie 2
```sql
select
order_id,
order_date,
status,
total_amount,
round(total_amount * 1.23, 2) as total_with_vat
from course.orders 
group by order_id, order_date, status, total_amount
order by total_with_vat desc 
limit 5;
```
## Zadanie 3
```sql
select
c.customer_name,
c.country,
o.order_id,
o.order_date,
o.total_amount
from course.customers c
join course.orders o
on c.customer_id = o.customer_id
order by total_amount desc;
```
## Zadanie 4
```sql
select
o.customer_id,
c.customer_name,
count(o.order_id) as orders_count
from course.customers c
join course.orders o
on c.customer_id = o.customer_id  
group by o.customer_id, customer_name
order by orders_count desc;
```
## Zadanie 5
```sql
select
c.country,
sum(o.total_amount) as total_revenue
from course.customers c
join course.orders o
on o.customer_id = c.customer_id
group by c.country
order by total_revenue desc;
```
## Zadanie 6
```sql
select 
status,
round(avg(total_amount),2)as average_order_value
from course.orders 
group by status
order by average_order_value desc;
```
## Zadanie 7
```sql
select
p.product_id,
p.product_name,
sum(oi.quantity) as units_sold
from course.products p
join course.order_items oi
on oi.product_id = p.product_id
group by p.product_id, p.product_name
having sum(oi.quantity) > 1;
```
## Zadanie 8
```sql
select
p.product_id,
p.product_name,
sum(oi.quantity * oi.unit_price) as sales_value
from course.products p
join course.order_items oi
on oi.product_id = p.product_id 
group by p.product_id, p.product_name
order by sales_value desc;
```
## Zadanie 9
```sql
select
    o.order_id,
    c.customer_name,
    o.total_amount,
    case
        when o.total_amount >= 150 then 'high'
        else 'standard'
    end as order_tier
from course.orders o
join course.customers c
    on c.customer_id = o.customer_id;
```
## Zadanie 10
```sql
select 
customer_id,
customer_name,
country
from course.customers
where customer_id not in(
select customer_id
from course.orders
);
```
## Zadanie 11
```sql
select distinct c.country, o.status
from course.customers c
join course.orders o
on c.customer_id = o.customer_id;
```
## Zadanie 12
```sql
select
customer_id,
customer_name
from course.customers 
where customer_name like '%A%' or customer_name like '%a%';
```
## Zadanie 13
```sql
select
c.customer_id,
c.customer_name,
count(o.order_id) as orders_count
from course.customers c
join course.orders o
on c.customer_id = o.customer_id 
group by c.customer_id, c.customer_name
having count(o.order_id) > 1;
```
## Zadanie 14
```sql

```
