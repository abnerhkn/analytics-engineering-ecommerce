# Sales Performance – Dimensional Data Model

## 1. Business Context

This project aims to analyze sales performance for an e-commerce business, focusing on revenue evolution, product performance, regional distribution, and seller contribution.

The dimensional model was designed to support analytical queries and BI tools such as Power BI and Looker, enabling fast aggregation, drill-down analysis, and time-based comparisons.

---

## 2. Grain Definition

**Fact Table Grain**

> One record represents **one item sold in an order**.

This grain was chosen to:
- Allow product-level analysis
- Ensure correct aggregation of revenue and quantities
- Avoid double counting at order level
- Support flexible slicing by customer, seller, product and time

---

## 3. Fact Table – `fact_sales`

The `fact_sales` table stores transactional sales data at item level.

### Fields

| Column Name | Description |
|------------|------------|
| order_id | Unique identifier of the order |
| order_item_id | Sequential item number within the order |
| order_date | Purchase date |
| product_id | Foreign key to product dimension |
| seller_id | Foreign key to seller dimension |
| customer_id | Foreign key to customer dimension |
| price | Item price |
| freight_value | Freight cost |
| revenue | Total revenue per item (`price + freight_value`) |

### Metrics

- **Total Revenue**
- **Total Items Sold**
- **Average Ticket**
- **Revenue Growth (MoM / YoY)**

---

## 4. Dimension Tables

### `dim_date`

Time dimension derived from the order purchase timestamp.

| Column | Description |
|------|------------|
| date | Calendar date |
| year | Year |
| month | Month number |
| month_name | Month name |
| year_month | Year and month (YYYY-MM) |

---

### `dim_product`

Product master data.

| Column | Description |
|------|------------|
| product_id | Product identifier |
| product_category_name | Product category |
| product_weight_g | Weight in grams |
| product_length_cm | Length |
| product_height_cm | Height |
| product_width_cm | Width |

---

### `dim_customer`

Customer location information.

| Column | Description |
|------|------------|
| customer_id | Customer identifier |
| customer_city | City |
| customer_state | State |

---

### `dim_seller`

Seller location information.

| Column | Description |
|------|------------|
| seller_id | Seller identifier |
| seller_city | City |
| seller_state | State |

---

## 5. Logical Model Diagram

```text
                    dim_date
                       |
dim_customer —— fact_sales —— dim_product
                       |
                  dim_seller
