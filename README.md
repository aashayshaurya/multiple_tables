# Project Overview
This project was developed as part of the **Database Management Systems (DBMS)** coursework.  
The goal was to take a retail/mall sales dataset and:

- Clean and normalize it into multiple related tables in SQLite.
- Establish foreign key relationships for efficient queries
- Write and run SQL queries using multi-table JOIN operations to extract insights.
- Generate visualizations for sales trends, customer behavior, and product performance.

The dataset contains customer demographics, product details, product categories, malls, invoice transactions, quantities sold, and payment methods.


## Contents
- **MULTIPLE_TABLE.ipynb** – Jupyter Notebook containing the entire workflow:
  - Data loading from CSV
  - Creation of SQLite tables
  - Data normalization
  - SQL queries for analysis
  - Visualization of results
- **Dataset (CSV)** – Raw sales dataset used in the project.
- **Database File (.db)** – SQLite database generated from the notebook.



## Database Scheme
**customer**
- `customer_id` (TEXT, Primary Key, Unique)
- `gender` (TEXT)
- `age` (TEXT)

**product**
- `product_id` (TEXT, Primary Key, Unique)
- `category` (TEXT)

**invoices**
- `invoice_no` (TEXT, Primary Key, Unique)
- `customer_id` (TEXT, Foreign Key → customer.customer_id)
- `invoice_date` (TEXT)
- `payment_method` (INT)
- `mall_name` (TEXT)

**invoices_detail**
- `product_id` (TEXT, Foreign Key → product.product_id)
- `invoice_no` (TEXT, Foreign Key → invoices.invoice_no)
- `quantity` (INT)
- `price` (INT)

---

## Key Relationships
- `customer.customer_id` → `invoices.customer_id` (one-to-many)
- `invoices.invoice_no` → `invoices_detail.invoice_no` (one-to-many)
- `product.product_id` → `invoices_detail.product_id` (one-to-many)
