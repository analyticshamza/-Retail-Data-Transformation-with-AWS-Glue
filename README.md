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

| Step                | Screenshot |
|---------------------|------------|
| **S3 Bucket Structure** | ![S3 Bucket Structure](https://github.com/user-attachments/assets/316e1e92-eb18-47f0-a09b-fa08d57d2323)<br>![S3 Folders](https://github.com/user-attachments/assets/fdf5793c-ec1c-44a7-9d24-ffc64e097d8c) |
| **Glue Crawlers**        | ![Crawler Setup](https://github.com/user-attachments/assets/62766695-d991-442a-9dd6-8b4f8319cc82)<br>![Crawler Config](https://github.com/user-attachments/assets/6d8a5e3b-3791-4331-86a9-38989c20d331) |
| **Data Catalog**         | ![Data Catalog](https://github.com/user-attachments/assets/6ca6adfd-50be-4249-8245-f47fca44e86d) |
| **Visual ETL Workflow** | ![Visual ETL](https://github.com/user-attachments/assets/1a451426-e8c3-462d-9ef4-dcca1ececf0d) |
| **S3 Select Query**      | ![S3 Select Query](https://github.com/user-attachments/assets/8b1f596c-c82a-416b-b7ad-af13e04b138a) |


## 🪪 License

This project is licensed under the [MIT License](LICENSE).
