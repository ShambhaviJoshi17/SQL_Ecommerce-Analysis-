****SQL_Ecommerce-Analysis****

![image](https://github.com/user-attachments/assets/a71332d8-0a46-4eec-bb11-03bff51fa60f)

![image](https://github.com/user-attachments/assets/5989f04a-6506-4b1c-a38c-4a3599c6d61b)

![image](https://github.com/user-attachments/assets/6edbfbdc-cc36-4ded-a895-35610b805685)

![image](https://github.com/user-attachments/assets/f4ac0dfb-1a56-42eb-83a0-2dbbb3cbd021)


***Ecommerce Sql Queries***

Use E_commerce;

-- 1) Weekday Vs Weekend (order_purchase_timestamp) Payment Statistics

 select 'Weekday', sum(payment_value) as Payment_Statistics from orders a inner join
 order_payments b on (a.order_id = b.order_id) where weekday(order_purchase_timestamp)<5
Union all
select 'Weekend', sum(payment_value) as Payment_Statistics from orders a inner join 
order_payments b on (a.order_id = b.order_id) where weekday(order_purchase_timestamp)>=5;

-- 2) Number of Orders with review score 5 and payment type as credit card.

select count(b.order_id) as Number_of_Orders from order_payments a inner join
order_reviews b on (a.order_id = b.order_id)
 where review_score = 5 and payment_type = 'Credit_card';
 
 -- 3) Average number of days taken for order_delivered_customer_date for pet_shop

select avg(order_delivered_customer_date) from orders a inner join order_items b
on (a.order_id= b.order_id) join products c on (b.product_id=c.product_id) 
where product_category_name = 'pet_shop';

-- 4) Average price and payment values from customers of sao paulo city

select Avg(price) from order_items a join orders b
on (a.order_id=b.order_id) join customers c on (b.customer_id=c.customer_id)
where customer_city= 'sao paulo';

select Avg(payment_value) from order_payments a join orders b
on (a.order_id=b.order_id) join customers c on (b.customer_id=c.customer_id)
where customer_city= 'sao paulo';

-- 5) Relationship between shipping days (order_delivered_customer_date - order_purchase_timestamp) Vs review scores.

select order_delivered_customer_date, order_purchase_timestamp, review_score from 
orders a join order_reviews b on (a.order_id=b.order_id);

![Joins](https://github.com/user-attachments/assets/380c06cd-0dbc-4399-9038-9f0752b3f82b)

