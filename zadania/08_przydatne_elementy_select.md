## Zadanie 1
```sql
select distinct country from course.customers;
```
## Zadanie 2
```sql
select distinct status from course.orders;
```
## Zadanie 3
```sql
select distinct category from course.products;
```
## Zadanie 4
```sql
select distinct country, acquisition_channel from course.customers;
```
## Zadanie 5
```sql
select customer_name,
upper(customer_name) as customer_name_upper
from course.customers;
```
## Zadanie 6
```sql
select email,
lower(email) as email_lower
from course.customers;
```
## Zadanie 7
```sql
select customer_name,
LENGTH(customer_name) as name_LENGTH
from course.customers;
```
## Zadanie 8
```sql
SELECT
    customer_name || ' - ' || country AS customer_label
FROM course.customers;
```

## Zadanie 9
```sql
select
order_id,
total_amount,
round(total_amount * 1.23,2) as total_with_vat
from course.orders;
```
## Zadanie 10
```sql
select round(avg(total_amount), 2) as average_order_value
from course.orders;
```
## Zadanie 11
```sql
select
customer_id,
customer_name,
coalesce(email, 'missing mail') as email
from course.customers;
```
## Zadanie 12
```sql
select 
order_id,
total_amount,
case 
	when total_amount >= 150 then 'high'
	else 'standard'
end as order_tier
from course.orders;
```
## Zadanie 13
```sql
select
order_item_id,
quantity,
unit_price,
quantity * unit_price as line_value
from course.order_items;
```
## Zadanie 14
```sql
select 
order_id,
cast(total_amount as int) as total_amount_as_int
from course.orders;
```
## Zadanie 15
```sql
select
customer_id,
customer_name,
upper(country) as country_upper,
coalesce(email, 'missing mail') as email
from course.customers;
```
## Zadanie 16
```sql
SELECT
    customer_id|| ' - ' || customer_name AS customer_label
FROM course.customers
order by customer_id;
```
## Zadanie 17
```sql
select
customer_id,
customer_name,
coalesce(email, 'brak emaila') as email_or_placeholder
from course.customers 
order by customer_id;
```
## Zadanie 18
```sql
select
product_id,
product_name,
base_price,
case 
	when base_price < 50 then 'budget'
	when base_price < 150 then 'standard'
	else 'premium'
end as price_bucket
from course.products 
order by product_id;
```
## Zadanie 19
```sql
select
order_id,
total_amount,
round(total_amount * 1.23, 2) as total_with_vat
from course.orders 
order by order_id;
```
## Zadanie 20
```sql
select distinct
UPPER(acquisition_channel) as channel from course.customers
order by channel;
```
