# E-Commerce Sales Analytics Engineering Project

## Business Question
How are sales performing over time and which products, regions, and sellers drive revenue growth?

## Business Context
This project simulates a production-grade analytics environment for an e-commerce business, focusing on sales performance, revenue analysis, and dimensional modeling to support BI and decision-making.

The main goal is to transform raw transactional data into a reliable analytical model optimized for BI tools.

---

## Scope
- Sales performance analysis
- Revenue, volume, and ticket metrics
- Time-based growth analysis (MoM / YoY)
- Product, seller, and regional breakdowns

Out of scope:
- Marketing attribution
- Inventory optimization
- Fraud detection
- Predictive modeling

---

## Dataset
**Brazilian E-Commerce Public Dataset (Olist)**  
Public dataset available on Kaggle, adapted to simulate a real-world analytics pipeline.

The original data is kept in raw format and transformed into analytical fact and dimension tables.

---

## Data Architecture

This project follows an **ELT (Extract, Load, Transform)** approach, organizing data into analytical layers:

- **Raw (`data/raw`)**  
  Original CSV files from the Kaggle dataset, preserved with minimal changes.

- **Model (`model`)**  
  Transformed and curated analytical tables, including fact and dimension models.

- **Dashboards (`dashboards`)**  
  Semantic and visualization layer built using BI tools.

This structure reflects common patterns used in modern analytics engineering teams.

---

## Data Model

The analytical model follows a **dimensional (star schema)** design, optimized for aggregation, drill-down analysis, and BI performance.

- Fact table at item-level grain
- Conformed dimensions for time, product, customer, and seller

Detailed documentation of the dimensional model is available in:
- `dimensional_model.md`

---

## Key Metrics

- Total Revenue
- Total Items Sold
- Number of Orders
- Average Ticket
- Revenue Growth (Month-over-Month, Year-over-Year)
- Sales by Product, Seller, and Region

Metric definitions are centralized to ensure consistency across dashboards.

---

## Tools
- SQL
- Power BI

The project is designed to be easily extended to other BI tools such as Looker.

---

## Project Structure

```text
analytics-engineering-ecommerce/
│
├── README.md
├── dimensional_model.md
│
├── data/
│   └── raw/
│
├── model/
│
├── dashboards/
│   └── power_bi/
