Introduction

This project focuses on analyzing pizza sales data using SQL queries. The goal is to demonstrate how raw transactional data can be transformed into meaningful business insights.
Pizza outlets generate a large amount of data daily—from customer orders and revenue to item preferences and time-based trends. Using SQL, 
<img width="2000" height="1200" alt="pizza_sales_er_diagram" src="https://github.com/user-attachments/assets/95cf6611-57a0-43bb-aeb8-7bcdc72da046" />
I explored this dataset to identify sales patterns,
revenue drivers, and operational insights.

🎯 Executive Summary

Key highlights of the project:

📊 Total orders and revenue analysis

🏆 Identification of best-selling pizzas

🕑 Sales distribution by hour and date

🍕 Most common pizza sizes & categories

💰 Revenue trends and top contributors

The results show how SQL can support data-driven business decisions such as inventory management, staffing optimization, and targeted promotions.

🛠️ Tools & Skills

SQL (SELECT, JOIN, GROUP BY, HAVING, ORDER BY, aggregate functions)

Relational Database concepts (tables for orders, pizzas, categories, customers)

Data Analysis for extracting business insights

📊 Key SQL Queries & Insights
1️⃣ Total Number of Orders
SELECT COUNT(order_id) AS total_orders
FROM orders;

2️⃣ Total Revenue Generated
SELECT ROUND(SUM(order_details.quantity * pizzas.price), 2) AS total_revenue
FROM order_details
JOIN pizzas ON order_details.pizza_id = pizzas.pizza_id;

3️⃣ Highest-Priced Pizza
SELECT pizza_name, price
FROM pizzas
ORDER BY price DESC
LIMIT 1;

4️⃣ Most Common Pizza Size Ordered
SELECT size, COUNT(order_details.order_id) AS total_orders
FROM pizzas
JOIN order_details ON pizzas.pizza_id = order_details.pizza_id
GROUP BY size
ORDER BY total_orders DESC
LIMIT 1;

5️⃣ Top 5 Most Ordered Pizza Types
SELECT pizza_name, SUM(order_details.quantity) AS total_quantity
FROM pizzas
JOIN order_details ON pizzas.pizza_id = order_details.pizza_id
GROUP BY pizza_name
ORDER BY total_quantity DESC
LIMIT 5;

6️⃣ Orders Distribution by Hour
SELECT HOUR(order_time) AS order_hour, COUNT(order_id) AS total_orders
FROM orders
GROUP BY order_hour
ORDER BY order_hour;
