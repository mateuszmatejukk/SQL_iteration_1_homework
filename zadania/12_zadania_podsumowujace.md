## Zadanie 1
```sql
select 
c.customer_id,
c.customer_name,
c.country,
c.acquisition_channel
from course.customers c
left join course.orders o
on c.customer_id = o.customer_id 	
count(order_id) as paid_orders_count
where o.status is 'paid',
count(o.order_id) as cancelled_orders_count
where o.status is 'cancelled',
sum(o.total_amount) as total_revenue,
avg(o.total_amount) as average_order_value,
case
	when order_id is null then 'no_orders'
	else 'buyer'
end
group by c.customer_id, c.customer_name, c.country, c.acquisition_channel
order by total_revenue desc;
```
## Zadanie 2
```sql
select
p.product_id,
p.product_name,
p.category,
p.base_price,
sum(oi.quantity) as units_sold,
sum(oi.quantity * oi.unit_price) as gross_revenue,
round(avg(oi.unit_price),2) as average_unit_price,
case 
	when order_item_id is null then 'not_sold'
	else 'sold'
end as sale_status
from course.products p
left join course.order_items oi
on oi.product_id = p.product_id
group by p.product_id, p.product_name, p.category, p.base_price, oi.order_item_id
order by gross_revenue desc;
```
## Zadanie 3
```sql
select
date_trunc('month',o.order_date) as sales_month,
c.country,
sum(o.order_id) as orders_count,
count(distinct(o.customer_id) as customers_count,
count(o.order_id) where status is 'paid',
count(o.order_id) where status is 'cancelled',
round(avg(o.total_amount),2) as average_order_value,
from course.orders o  
join course.customers c 
on c.customer_id = o.customer_id;
```
## Zadanie 4
```sql

```
