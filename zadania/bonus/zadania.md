## Zadanie 1
```sql
with customer_revenue as(
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
	having count(o.order_id) >= 2
	)
	
select
customer_id,
customer_name,
country,
orders_count,
total_revenue,
average_order_value,
case when
    total_revenue > (
    select
    avg(total_revenue)
    from customer_revenue
    ) then 'above_average'
end as customer_revenue_tier
from customer_revenue
where total_revenue > (
    select
    avg(total_revenue)
    from customer_revenue
    )
order by total_revenue desc;
```
