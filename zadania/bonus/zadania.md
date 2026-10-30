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
