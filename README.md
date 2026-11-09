# E-commerce Inventory Data Analysis Using SQL

This project is implement for:

Data Analyst aspirants who want to build a strong Portfolio Project for interviews and LinkedIn
Anyone learning SQL hands-on
Preparing for interviews in retail, e-commerce, or product analytics

## Project Overview
The goal is to simulate how real-world data analysts work in the e-commerce and retail industries using SQL to:

✅ Database Setup: Create an e-commerce inventory database and import real-world product data.

✅ Exploratory Data Analysis (EDA): Explore product categories, stock availability, product quantities, and pricing inconsistencies.

✅ Data Cleaning: Handle missing values (NULL), remove invalid records, identify duplicates, and convert product prices from paise to rupees.

✅ Business Analysis: Write practical SQL queries to analyze product pricing, discounts, inventory levels, stock availability, and revenue.

✅ Business Insights: Identify best-selling products, high-revenue categories, low-stock products, and pricing trends to support better business decisions.

# Project Goal: 
Develop practical SQL skills by solving real-world e-commerce business problems using PostgreSQL.


📁 Dataset Overview
The dataset was sourced from Kaggle. It mimics what you'd typically encounter in a real-world e-commerce inventory system.

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility- exactly how real catalog data looks.

🧾 Columns:

- sku_id: Unique identifier for each product entry (Synthetic Primary Key)

- name: Product name as it appears on the app

- category: Product category like Fruits, Snacks, Beverages, etc.

- mrp: Maximum Retail Price (originally in paise, converted to ₹)

- discountPercent: Discount applied on MRP

- discountedSellingPrice: Final price after discount (also converted to ₹)

- availableQuantity: Units available in inventory

- weightInGms: Product weight in grams

- outOfStock: Boolean flag indicating stock availability

- quantity: Number of units per package (mixed with grams for loose produce)


🔧 Project Workflow

Here's a step-by-step breakdown of what we do in this project:
1. Database & Table Creation
We start by creating a SQL table with appropriate data types:

```
    CREATE TABLE shiblu (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(10,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(10,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
); 
```

2. Data Import
- Loaded CSV using pgAdmin's import feature.

- If you're not able to use the import feature, write this code instead:
```
   \copy shiblu(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
  FROM 'data/shiblu.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'WIN1252');
```
- Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV WIN1252 format.

3. 🔍 Data Exploration
- Counted the total number of records in the dataset

- Viewed a sample of the dataset to understand structure and content

- Checked for null values across all columns

- Identified distinct product categories available in the dataset

- Compared in-stock vs out-of-stock product counts

- Detected products present multiple times, representing different SKUs

4. 🧹 Data Cleaning
- Identified and removed rows where MRP or discounted selling price was zero

- Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability

5. 📊 Business Insights
- Found top 10 best-value products based on discount percentage

- Identified high-MRP products that are currently out of stock

- Estimated potential revenue for each product category

- Filtered expensive products (MRP > ₹500) with minimal discount

- Ranked top 5 categories offering highest average discounts

- Calculated price per gram to identify value-for-money products

- Grouped products based on weight into Low, Medium, and Bulk categories

- Measured total inventory weight per product category

🛠️ How to Use This Project
1. Clone the repository

```
git clone https://github.com/arfinmahmudshiblu/PostgreSQL_project.git
```

2. Open zepto_SQL_data_analysis.sql

This file contains:

- Table creation

- Data exploration

- Data cleaning

- SQL Business analysis

3. Load the dataset into pgAdmin or any other PostgreSQL client

- Create a database and run the SQL file

- Import the dataset (convert to WIN1252 if necessary)


📜 License
MIT --- feel free to fork, star, and use in your portfolio.


👨‍💻 About the Author
Hello, My name's Arfin Mahmud - a Data Scientist. I break down complex data topics into simple, practical content that actually helps you land a job.





