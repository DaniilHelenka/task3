# sqlQueries

1) Calculate the total sales volume for March 2024:

SELECT SUM(amount) as march_sales
FROM orders
WHERE strftime('%Y-%m', order_date) = '2024-03';

2) Find the customer who spent the most overall:

SELECT 
    customer,
    SUM(amount) as total_spent
FROM orders
GROUP BY customer
ORDER BY total_spent DESC
LIMIT 1;

3) Calculate average order value for the last three months:

SELECT AVG(amount) as avg_order_value
FROM orders
WHERE order_date >= date('now', '-3 months')
AND order_date <= date('now');
