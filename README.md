# Superstore Data Engineering Project

This project demonstrates a complete **ETL (Extract, Transform, Load)** pipeline. It takes raw retail data from a CSV file, normalizes it into a **3rd Normal Form (3NF)** relational structure, and loads it into a **PostgreSQL** database using Python and SQLAlchemy.

## Project Deliverables

* **PostgreSQL Database:** `superstore_db` with 7 interconnected and normalized tables.
* **Python Script:** A Jupyter Notebook (`week6.ipynb`) managing the end-to-end process.
* **Relational Integrity:** Full implementation of Primary and Foreign Keys.
* **Analytical Views:** SQL Views for business intelligence and rapid reporting.

---

## Database Architecture (ERD)

The database is designed to eliminate data redundancy and ensure referential integrity.

### **Tables Created:**

1. **regions** : Geographical regions.
2. **states** : States linked to specific regions.
3. **categories** : Product categories.
4. **products** : Individual products linked to categories.
5. **customers** : Customer profiles linked to states.
6. **orders** : High-level order information (dates, shipping).
7. **order_details** : Transactional fact table (sales, quantity, profit).

---

## Execution Steps

The project follows a strict 5-step workflow:

1. **Step 1: Cleanup & Connection** - Establishes the SQLAlchemy engine and clears any existing tables to allow for idempotent runs.
2. **Step 2: Normalization** - Uses Pandas to split the flat file into logical entities and generate unique IDs.
3. **Step 3: Loading & Linking** - Data is pushed to PostgreSQL. **Primary Keys** and **Foreign Keys** are established via SQL `ALTER` commands to link the tables.
4. **Step 4: Transformations** - Creation of SQL Views (e.g., `vw_sales_summary`) to pre-calculate total sales and profits.
5. **Step 5: Verification** - Automated row-count comparison between the source Pandas DataFrames and the final SQL tables.

---

## Analytical Insights

Once the pipeline runs, you can immediately query business metrics:

* **Sales Performance:** Aggregate sales by Region and Category.
* **Shipping Efficiency:** Calculation of delivery delays using native SQL date formats.
* **Customer Loyalty:** Ranking segments by lifetime value (LTV).

---

## Tech Stack

* **Language:** Python 3.x
* **Libraries:** Pandas, SQLAlchemy, Psycopg2
* **Database:** PostgreSQL 16
* **Tools:** VS Code, Jupyter Notebook, pgAdmin 4

---

### **How to Install & Run**

1. Ensure **PostgreSQL** is running on `localhost:5432`.
2. Create a database named `superstore_db`.
3. Install requirements:
   **Bash**

   ```
   pip install pandas sqlalchemy psycopg2
   ```
4. Run all cells in `week6.ipynb`.
