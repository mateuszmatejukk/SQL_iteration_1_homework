# Zadania 03 - wybór kolumn i aliasy

## Zadanie 1
```sql 
select customer_id, customer_name, country 
from course.customers;
```

## Zadanie 2
```sql
select product_id, product_name, base_price
from course.products;
```
# Zadanie 3
```sql
select order_id, order_date, total_amount 
from course.orders;
```
# Zadanie 4
```sql
select customer_name as name from course.customers;
```
# Zadanie 5
```sql
select total_amount as order_total from course.orders;
```
# Zadanie 6
```sql
select product_name as name, base_price as price from course.products;
```
# Zadanie 7
```sql
select 
order_id, 
total_amount, 
total_amount * 1.23 as total_with_vat 
from course.orders;
```
# Zadanie 8
```sql
select 
order_item_id, 
quantity, 
unit_price,
quantity * unit_price as line_value
from course.order_items;
```
# Zadanie 9
```sql
select customer_name, country, signup_date from course.customers;
```
# Zadanie 10
Alias zmienia nazwę tylko w wyniku zapytania, nie zmienia danych w bazie.
