## Zadanie 1
```sql
with value_total as(
	select
	c.customer_id,
	c.customer_name,
	c.country,
	count(o.order_id) as orders_count,
	sum(o.total_amount) as total_revenue,
	avg(o.total_amount) as average_order_value
	from course.customers c
	join course.orders o
	on c.customer_id = o.customer_id 
	group by c.customer_id, c.customer_name, c.country
	having count(o.order_id) >=2 
	)
select * 
from value_total
where total_revenue > (
select avg(total_revenue)
from value_total)
order by total_revenue desc;
```
## Zadanie 2
```sql
with monthly_sales as(
	select
	date_trunc('month',o.order_date) as sales_month,
	o.status,
	count(o.order_id) as orders_count,
	count(distinct o.customer_id) as customers_count,
	sum(o.total_amount) as total_revenue,
	avg(o.total_amount) as average_order_value
	from course.orders o
	group by date_trunc('month',o.order_date), o.status
	),
sum_of_sales as(
select
sales_month,
sum(total_revenue) as total_sum
from monthly_sales
group by sales_month
)
select 
ms.sales_month,
status,
orders_count,
customers_count,
total_revenue,
average_order_value,
round((total_revenue / total_sum) * 100,2)  as status_share_in_month
from monthly_sales ms
join sum_of_sales sos
on mv.sales_month = sos.sales_month;
```
## Zadanie 3
```sql
with product_sales as(
	select
	p.product_id,
	p.product_name,
	p.category,
	count(oi.quantity) as units_sold,
	sum(oi.unit_price) as product_revenue
	from course.products p
	join course.order_items oi
	on p.product_id = oi.product_id
	group by p.product_id, p.product_name, p.category
	),
sales_per_category as(
	select
	category,
	avg(product_revenue) as category_average_revenue 
	from product_sales 
	group by category
	)
select 
product_id,
product_name,
ps.category,
units_sold,
product_revenue,
category_average_revenue 
from product_sales ps
join sales_per_category spc
on ps.category = spc.category
where product_revenue > category_average_revenue 
order by ps.category, product_revenue desc
```
## Zadanie 4
```sql
select 
'customer_without_order' as issue_type,
c.customer_id as object_id,
c.customer_name as object_name,
count(o.customer_id) as metric_value
from course.customers c
left join course.orders o 
where o.customer_id is null

union all

select
'products_without_sales' as issue_type,
p.product_id as object_id,
p.product_name as object_name,
count(oi.product_id) as metric_value
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id 
where oi.product_id is null

union all
```
## Zadanie 5
```sql
with difference_checker as(
	select
	o.order_id,
	c.customer_name,
	o.status,
	o.total_amount as order_total_amount,
	sum(oi.quantity * oi.unit_price) as items_total_amount
	from course.orders o 
	left join course.order_items oi
	on o.order_id = oi.order_id 
	left join course.customers c
	on c.customer_id = o.customer_id 
	group by o.order_id, c.customer_name, o.status, o.total_amount
	),
amount_check as(
select difference_checker *
(order_total_amount - items_total_amount) as difference_amount,
case 
	when (order_total_amount - items_total_amount)  is null then 'missing items'
	when (order_total_amount - items_total_amount)  = 0 then 'match'
	when (order_total_amount - items_total_amount) <> 0 then 'different'
	end as amount_check
from difference_checker)
select 
order_id,
customer_name,
status,
order_total_amount,
items_total_amount
from amount_check
where amount_check <> 'match'
order by amount_check, order_id;
```
## Zadanie 6
```sql
with country_per_category as(
	select
	c.country,
	count(distinct c.customer_id) as customers_count,
	count(o.order_id) as orders_count,
	count(distinct p.category) as categories_count,
	sum(oi.quantity * oi.unit_price) as total_revenue
	from course.customers c 
	join course.orders o 
	on c.customer_id = o.customer_id 
	join course.order_items oi
	on o.order_id = oi.order_id 
	join course.products p
	on p.product_id = oi.product_id
	group by c.country
	)
select * 
from country_per_category 
where categories_count >= 2 and total_revenue > 100
order by categories_count desc, total_revenue desc;
```
## Zadanie 7
```sql
with less_valuable_customers as(
	select
	c.customer_id,
	c.customer_name,
	c.country,
	sum(o.total_amount) as total_revenue,
	count(o.order_id) as orders_count
	from course.customers c
	join course.orders o
	on c.customer_id = o.customer_id
	where exists(
	select 1
	from course.products p
	where p.category = 'course')
	group by c.customer_id, c.customer_name, c.country
	)
select * from less_valuable_customers;
```

