# Enterprise E-Commerce Data Warehouse & Automated ETL Pipeline

## Project Overview

This project takes a raw 1 million row e-commerce transaction file and restructures it into a proper relational database using Python and SQL. The goal was to show how early-stage startups can move from messy flat data files to a clean, queryable data warehouse that supports faster business decisions.

## Tools Used

- Python (Pandas) — data cleaning and transformation
- SQL (SQLite) — database creation and querying
- Google Colab
- Dataset: 1 million e-commerce transactions

## Business Question

How can a startup transform a large unstructured transaction file into an organized database that makes reporting faster and more reliable?

## Approach

Built a Star Schema database with four tables:

- **dim_users** — customer profiles and locations
- **dim_products** — product categories, brands and pricing
- **dim_sellers** — seller information and ratings
- **fact_sales** — all transaction records linking back to the above tables

This structure reduces data redundancy and makes queries significantly faster than scanning a single million row file.

## Key Findings

**Category Performance:**

|Category   |Units Sold|Avg Shipping|Return Rate|Total Revenue|
|-----------|----------|------------|-----------|-------------|
|Electronics|201,475   |3.17 days   |11.62%     |$2.40B       |
|Home       |202,528   |3.16 days   |11.56%     |$1.97B       |
|Sports     |198,487   |3.17 days   |11.64%     |$1.90B       |
|Clothing   |198,740   |3.16 days   |11.53%     |$1.83B       |
|Beauty     |198,770   |3.17 days   |11.64%     |$1.82B       |

**Top Brands by Revenue:**

- Electronics — Boat ($211M) and Samsung ($207M)
- Home — Puma ($175M) and Nike ($169M)

**Note on dataset:** The source data was synthetically generated which caused some brands to appear in incorrect categories. This was identified during analysis and flagged — it does not affect the accuracy of the SQL queries or pipeline logic.

## SQL Techniques Used

- CTEs (Common Table Expressions)
- Window functions for brand ranking per category
- Multi-table joins across all four dimension tables

## Business Recommendations

1. Electronics generates the highest revenue at $2.40B but also has the highest return rate — investigating return reasons could recover significant revenue
1. Shipping time is consistent across all categories at ~3.17 days — any improvement here would benefit all verticals equally
1. Moving from flat files to this star schema structure reduces query time significantly as the business scales

## Dataset Source

Kaggle — E-commerce transactions dataset


