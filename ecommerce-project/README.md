# E-commerce Demo Project

This project contains synthetic e-commerce data (large dataset) and scripts to ingest into SQLite.

## Structure
```
ecommerce-project/
├── data/
│   ├── users.csv
│   ├── products.csv
│   ├── orders.csv
│   ├── order_items.csv
│   └── payments.csv
├── db/
│   └── ecommerce.db
├── scripts/
│   ├── ingest_data.py
│   └── create_tables.sql
└── README.md
```

## How to use
1. Clone the repo and `cd` into it.
2. (Optional) Inspect the CSV files in `data/`.
3. To create the SQLite DB and ingest data, run:
```bash
python3 scripts/ingest_data.py
```
This will create `db/ecommerce.db`.

## Example SQL query (join multiple tables)
```sql
SELECT u.name AS customer_name,
       p.name AS product_name,
       oi.quantity,
       o.order_date,
       o.total_amount
FROM orders o
JOIN users u ON o.user_id = u.user_id
JOIN order_items oi ON oi.order_id = o.order_id
JOIN products p ON p.product_id = oi.product_id
LIMIT 100;
```

