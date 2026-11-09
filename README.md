# Week 1 Database Assignment: Clothes Shop Management System

A MySQL database that stores the customers, stock and sales of a clothes shop, like a boutique or a mitumba shop.

## Database name
`clothes_shop_db`

## Tables

| Table | Purpose | Columns |
|---|---|---|
| `customers` | People who buy | customer_id, full_name, phone, town |
| `products` | Clothes in stock | product_id, product_name, category, size, price, stock_quantity |
| `orders` | One row per sale | order_id, customer_id, order_date, payment_method |
| `order_items` | The items in each sale | order_item_id, order_id, product_id, quantity |

## How the tables connect
- One customer can have many orders (`orders.customer_id` links to `customers`).
- One order can have many items (`order_items.order_id` links to `orders`).
- Each item is one product (`order_items.product_id` links to `products`).

## Design choices
- Every table has an auto-numbered `PRIMARY KEY`.
- Foreign keys stop a sale from being recorded for a customer or product that doesn't exist.
- `phone` is text, so numbers keep their leading zero.
- `price` uses `DECIMAL(10,2)` for exact money values.
- `order_date` fills in automatically with the date and time of the sale.

## How to run

**Terminal:**
```bash
mysql -u root -p
```
```sql
source answer.sql
```

**MySQL Workbench:** open `answer.sql` and click the lightning bolt.

## Check it worked
```sql
USE clothes_shop_db;
SHOW TABLES;
```
You should see 4 tables.
