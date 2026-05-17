# Enterprise E-Commerce Data Warehouse & Automated ETL Pipeline

## 📌 Project Overview
Early-stage startups frequently scale using flat, denormalized event ledgers that quickly bottleneck operations. This project demonstrates backend data engineering infrastructure at scale by ingesting a massive, 1,000,000-row raw transactional ledger and reverse-engineering it into an optimized relational Star Schema warehouse using an automated Python-to-SQL ETL pipeline.

## 🛠️ Tech Stack & Database Architecture
* **Core Technologies:** Python (Pandas), SQL (SQLite3 Engine) via Google Colab
* **Data Modeling:** Star Schema Optimization (Separating transactional Fact metrics from descriptive entity Dimensions)
* **Advanced Querying Techniques:** CTEs (Common Table Expressions), Window Functions (`ROW_NUMBER() OVER`), Multilevel Joins, and Relational Partitions

---

## 🧬 The Structural Transformation (Star Schema Mapping)
The pipeline automatically parses the incoming stream and normalizes the attributes into the following indexed analytical schema:
* `dim_users`: Normalizes unique profile attributes (`user_id`, `location`, `device`)
* `dim_products`: Clusters asset definitions (`product_id`, `category`, `subcategory`, `brand`, `price`)
* `dim_sellers`: Tracks merchant metrics (`seller_id`, `seller_rating`)
* `fact_sales`: Contains foreign keys and immutable transactional metrics (`final_price`, `discount`, `shipping_time_days`, `is_returned`)

---

## 📊 Automated SQL Audit Reports & Analytical Outtakes

### 1. Logistics Metrics & Category Revenue Optimization
The engine runs multi-table joins to monitor fulfillment risk and calculate total gross revenue streams:
* **Electronics:** 201,475 units sold | Avg Shipping: 3.17 Days | Return Rate: 11.62% | **Total Revenue: $2.40B**
* **Home:** 202,528 units sold | Avg Shipping: 3.16 Days | Return Rate: 11.56% | **Total Revenue: $1.97B**
* **Sports:** 198,487 units sold | Avg Shipping: 3.17 Days | Return Rate: 11.64% | **Total Revenue: $1.90B**
* **Clothing:** 198,740 units sold | Avg Shipping: 3.16 Days | Return Rate: 11.53% | **Total Revenue: $1.83B**
* **Beauty:** 198,770 units sold | Avg Shipping: 3.17 Days | Return Rate: 11.64% | **Total Revenue: $1.82B**

### 2. High-Performance Merchant Ranking (SQL Window Functions)
Using partitioned CTEs and ranking window constraints, the warehouse extracts the Top 2 revenue-generating brands for every single vertical:
* **Electronics Top Performers:** Boat ($211.37M) & Samsung ($207.47M)
* **Home Top Performers:** Puma ($175.80M) & Nike ($169.62M)

> 🔬 **Pipeline Diagnostic Outtake (Data Realism Audit):** During the execution phase, the query engine exposed an amusing characteristic within the synthetic dataset's generation logic. The probabilistic model cross-mapped product brands erroneously into alternative verticals—resulting in **Apple** and **Lenovo** surfacing as the top two highest-revenue brands within the *Clothing* segment, and **Zara** and **Samsung** dominating the *Beauty* column. This highlights the engine's absolute precision in surfacing accurate query outputs exactly as raw data maps them.

---

## 🏢 Business Strategy Impact for Scaling Startups
1. **Unlocks Blazing Fast Analytical Sub-Queries:** Moving from a giant, 1-million-row flat file to an indexed dimensional schema reduces storage redundancy and accelerates analytical processing speeds across company operations.
2. **Standardizes Merchant Integrity Checks:** Isolating `dim_sellers` allows internal product teams to monitor seller compliance metrics asynchronously without having to scan the entire transactional history ledger.
