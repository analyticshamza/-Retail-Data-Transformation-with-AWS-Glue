# 🛒 Retail Data Transformation with AWS Glue

This project demonstrates how to use **AWS Glue Visual ETL** to clean, transform, and join fragmented retail data stored in CSV format across Amazon S3. The goal is to simulate a real-world data pipeline for an e-commerce analytics use case.

---

## 📌 Project Objective

The objective of this project is to:
- Consolidate retail `products.csv` and `orders.csv` files from Amazon S3
- Use **AWS Glue Crawlers** to create Data Catalog tables
- Clean and align schemas using **Change Schema**
- Join datasets using **Join** transform
- Export the final processed data back to S3
- Query the results using **S3 Select** with SQL

---

## 🧱 Tech Stack

- **AWS S3** – Object storage for raw and processed data  
- **AWS Glue** – Crawlers, Data Catalog, Visual ETL  
- **AWS IAM** – Role-based access control for Glue services  
- **SQL** – Used via S3 Select for querying final output

---


## ✅ Steps Performed

### 1. **S3 Bucket Setup**
- Created bucket: `retail-detail`
- Created folder structure: `product-data/products-files` and `product-data/orders-files`
- Uploaded `products.csv` and `orders.csv` to respective folders

### 2. **AWS Glue Setup**
- Created database: `orders-db`
- Created two crawlers:
  - `prd-crawler` → for `products-files`
  - `ord-crawler` → for `orders-files`
- Ran crawlers to populate Glue Data Catalog tables

### 3. **ETL Pipeline (Visual ETL in AWS Glue Studio)**
- Used two data source blocks for `products` and `orders`
- Applied **Change Schema** to:
  - Rename mismatched fields (e.g., `prod_id` → `product_id`)
  - Match data types
- Applied **Join** to combine data on `product_id`
- Sent the final output to an S3 target folder

### 4. **Output and Query**
- Output file: `run-*.csv` saved back to S3
- Queried the results using **S3 Select** with SQL

---

## 🖼️ Screenshots

| Step | Screenshot |
|------|------------|
| S3 Bucket Structure | ![S3 Structure](screenshots/s3-structure.png) |
| Glue Crawlers | ![Glue Crawlers](screenshots/glue-crawlers.png) |
| Data Catalog | ![Data Catalog](screenshots/data-catalog.png) |
| Visual ETL Workflow | ![ETL Workflow](screenshots/visual-etl.png) |
| Output File | ![Output](screenshots/output-file.png) |
| S3 Select Query | ![S3 Select](screenshots/s3-select-query.png) |

## 🪪 License

This project is licensed under the [MIT License](LICENSE).
