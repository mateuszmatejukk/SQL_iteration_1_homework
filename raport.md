/*Przygotuj jeden raport kontrolny pokazujący sytuacje, które wymagają sprawdzenia przez zespół sprzedaży/analityki.
Wynik powinien zawierać kolumny:
- alert_type
- object_id
- object_name
- metric_value
- details
Raport ma składać się z 3 części
Pokaż w nim:
1. Klientów bez żadnego zamówienia.
   - alert_type: customer_without_order,
   - object_id: customer_id,
   - object_name: customer_name,
   - metric_value: 0.
2. Produkty, które nigdy się nie sprzedały.
   - alert_type: product_without_sale,
   - object_id: product_id,
   - object_name: product_name,
   - metric_value: 0.
3. Klientów, którzy wydali łącznie więcej niż 300.
   - alert_type: high_value_customer,
   - object_id: customer_id,
   - object_name: customer_name,
   - metric_value: suma wartości zamówień klienta.
*/
select 
'customer_without order' as alert_type,
c.customer_id as object_id,
c.customer_name as object_name,
0 as metric_value
from course.customers c 
left join course.orders o
on c.customer_id = o.customer_id
where o.order_id is null

union all

select
'product_without_sale' as alert_type,
p.product_id as object_id,
p.product_name as object_name,
0 as metric_value
from course.products p 
left join course.order_items oi
on p.product_id = oi.product_id 
where oi.order_item_id is null

union all 
select 
'high_value_customer' as alert_type,
o.customer_id as object_id,
c.customer_name as object_name,
sum(o.total_amount) as metric_value
from course.customers c
join course.orders o  
on c.customer_id = o.customer_id
group by o.customer_id, c.customer_name
having sum(o.total_amount) > 300

order by alert_type;
