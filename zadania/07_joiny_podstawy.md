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
