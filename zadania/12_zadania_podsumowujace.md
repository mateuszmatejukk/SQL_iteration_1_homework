## Zadanie 1
```sql
select 
c.customer_id,
c.customer_name,
c.country,
c.acquisition_channel,
sum(o.order_id) as orders_count,
SUM(CASE WHEN o.status = 'paid' THEN 1 ELSE 0 END) AS paid_orders_count,
    SUM(CASE WHEN o.status = 'cancelled' THEN 1 ELSE 0 END) AS cancelled_orders_count,
sum(o.total_amount) as total_revenue,
round(avg(o.total_amount),2),
case 
	when o.order_id is null then 'no_orders'
	else 'buyer'
end as customer_status
from course.customers c
left join course.orders o 
on c.customer_id = o.customer_id
group by c.customer_id, o.order_id
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
count(oi.order_id) as orders_count,
sum(oi.quantity * oi.unit_price) as gross_revenue,
round(avg(oi.unit_price),2) as average_unit_price,
case 
	when oi.order_id is null then 'not_sold'
	else 'sold'
end as sale_status
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id 
group by p.product_id, oi.order_id
order by gross_revenue desc;
```
## Zadanie 3
```sql
select
DATE_TRUNC('month', o.order_date) AS sales_month,
c.country,
count(o.order_id) as orders_count,
count(distinct(c.customer_id)) as customers_count,
SUM(CASE WHEN o.status = 'paid' THEN 1 ELSE 0 END) AS paid_orders_count,
    SUM(CASE WHEN o.status = 'cancelled' THEN 1 ELSE 0 END) AS cancelled_orders_count,
sum(o.total_amount) as total_revenue,
round(avg(o.total_amount),2) as average_order_value
from course.customers c
left join course.orders o
on c.customer_id = o.customer_id
group by c.country, sales_month
having sum(o.total_amount) > 100
order by sales_month, total_revenue desc;
```
## Zadanie 4
```sql

```

## Zadanie 5
```sql
select
'customer_without_order' as issue_type,
c.customer_id as object_id,
c.customer_name as object_name,
'Customer has no orders' as details
from course.customers c 
left join course.orders o 
on c.customer_id = o.customer_id 
where o.order_id is null

union all

select
'product_without_sale' as issue_type,
oi.product_id as object_id,
p.product_name as object_name,
'Product has not been purchased' as details
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id
where oi.product_id is null

union all 

select
'orders without order items' as issue_type,
o.order_id as object_id,
o.status as object_name,
'Order has no order items' as details
from course.orders o
left join course.order_items oi 
on o.order_id = oi.order_id 
where oi.order_item_id is null

union all

select 
'customer_without_email' as issue_type,
c.customer_id as object_id,
c.customer_name as object_name,
'Customer has no email' as details
from course.customers c
where c.email is null
order by issue_type, object_id;
--nie wiedziałem co dać jako object id w product without sale wiec dalem ten status zeby nie wywalalo mi bledu i ten raport sie pokazal
```
## Zadanie 6
```sql
select
o.order_id,
c.customer_name,
o.status,
o.total_amount as order_total_amount,
items.items_total_amount as items_total_amount,
(o.total_amount - items.items_total_amount) as difference_amount,
case 
	when (o.total_amount  -items.items_total_amount) = 0 then 'match'
	else 'different'
end as amount_check
from course.orders o  
join course.customers c
on o.customer_id = c.customer_id 
left join (
select 
oi.order_id as order_id,
sum(oi.quantity * oi.unit_price) as items_total_amount
from course.order_items oi
group by oi.order_id) items 
on items.order_id = o.order_id
order by (CASE WHEN o.total_amount - items.items_total_amount  = 0 THEN 1 ELSE 0 END);
```
## Zadanie 7
```sql
select 
c.acquisition_channel,
count(c.customer_id) as customers_count,
count(o.customer_id) as customers_with_orders_count,
count(o.order_id) as orders_count,
count(CASE WHEN o.status = 'paid' THEN 1 ELSE 0 END) AS paid_orders_count,
sum(o.total_amount) as total_revenue,
sum(o.total_amount) / count(c.customer_id) as average_revenue_per_customer
from course.customers c 
left join course.orders o
on o.customer_id = c.customer_id
group by c.acquisition_channel
order by total_revenue desc;
```
