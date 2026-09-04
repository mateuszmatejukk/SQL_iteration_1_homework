## Zadanie 1
select
order_id,
total_amount
from course.orders
where total_amount > (
select avg(total_amount)
from course.orders
);

## Zadanie 2
select 
customer_id,
customer_name
from course.customers
where customer_id in(
select customer_id
from course.orders
);

## Zadanie 3
select
customer_id,
customer_name
from course.customers
where customer_id not in(
select customer_id
from course.orders
);

## Zadanie 4
