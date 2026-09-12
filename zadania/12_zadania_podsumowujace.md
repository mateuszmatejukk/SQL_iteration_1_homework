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
where oi.order_id is null

/zamowienia bez pozycji zamowienia

select 
'customer_without_email' as
```
