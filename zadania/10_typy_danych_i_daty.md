## Zadanie 1
```sql
select
table_name,
column_name,
data_type
FROM information_schema.columns
where table_schema = 'course'
order by table_name, ordinal_position;
```
## Zadanie 2
```sql
select 
order_id,
cast(total_amount as int) as total_as_int
from course.orders;
```
## Zadanie 3
```sql
select
order_id,
order_date,
total_amount
from course.orders 
where order_date >='2026-05-10'
```
## Zadanie 4
```sql
select
order_id,
order_date,
total_amount
from course.orders 
where order_date between '2026-05-01' and '2026-05-10';
```
## Zadanie 5
```sql
select order_id,
 order_date,
extract(year from order_date) as order_year,
extract(month from order_date) as order_month,
extract (day from order_date) as order_day
from course.orders;
```
## Zadanie 6
```sql
select 
date_trunc('month', order_date) as sales_month,
sum(total_amount) as total_revenue
from course.orders 
group by date_trunc('month', order_date)
order by sales_month;
```
## Zadanie 7
```sql

```
## Zadanie 8
```sql
select current_date as date, 
current_timestamp as now;
```
### Zadanie 9
```sql
select current_date - interval '7 days' as seven_days_ago;
```
## Zadanie 10
```sql
select
order_id,
TO_CHAR(order_date, 'YYYY-MM') as order_months
from course.orders;
```
## Zadanie 11
```sql
select
order_id,
order_date,
current_date - order_date as order_age_days
from course.orders;
```
## Zadanie 12
```sql
select
    date_trunc('day', order_date) as day_of_week,
    sum(total_amount) as total_revenue
from course.orders
group by('day', order_date)
order by day_of_week;
```
## Zadanie 13
```sql
select
order_id,
order_date,
order_date + interval '7 days' as ship_deadline
from course.orders
group by order_id, order_date 
order by order_id;
```
## Zadanie 14
```sql

```
## Zadanie 15
```sql

```
## Zadanie 16
```sql
select
date_trunc('week', order_date) as sales_week,
sum(total_amount) as total_revenue
from course.orders 
group by date_trunc('week',order_date)
order by sales_week;
```
