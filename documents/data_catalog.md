# Data Catalog for Gold Layer

## Overview
The Gold Layer provides a business-level data view designed to support analytics and reporting. It is organized into **dimension tables** and **fact tables**, each structured for specific business metrics.

---

### 1. **gold.dim_customers**
- **Purpose:** Holds detailed customer information enriched with demographic and geographic attributes.
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| customer_key     | INT           | Unique surrogate key identifying each customer record.                                        |
| customer_id      | INT           | Unique numeric identifier for each customer.                                                  |
| customer_number  | NVARCHAR(50)  | Alphanumeric code used for tracking and identification of customers.                          |
| first_name       | NVARCHAR(50)  | First name of the customer as recorded in the system.                                         |
| last_name        | NVARCHAR(50)  | Surname or family name of the customer.                                                       |
| country          | NVARCHAR(50)  | Country where the customer resides (e.g., 'Australia').                                       |
| marital_status   | NVARCHAR(50)  | Marital status of the customer (e.g., 'Married', 'Single').                                   |
| gender           | NVARCHAR(50)  | Gender of the customer (e.g., 'Male', 'Female', 'n/a').                                       |
| birthdate        | DATE          | Birthdate of the customer in YYYY-MM-DD format (e.g., 1971-10-06).                            |
| create_date      | DATE          | Date when the customer record was created.                                                    |

---

### 2. **gold.dim_products**
- **Purpose:** Describes products and their various attributes.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| product_key         | INT           | Unique surrogate key for each product record.                                                 |
| product_id          | INT           | Unique internal identifier for tracking and referencing products.                             |
| product_number      | NVARCHAR(50)  | Structured alphanumeric code that categorizes or identifies the product for inventory.        |
| product_name        | NVARCHAR(50)  | Detailed name describing the product including key attributes like type, color, and size.     |
| category_id         | NVARCHAR(50)  | Unique identifier for the product's category, linking to a broader classification.            |
| category            | NVARCHAR(50)  | General classification of the product (e.g., Bikes, Components).                              |
| subcategory         | NVARCHAR(50)  | Detailed classification within the category, such as type of product.                         |
| maintenance_required| NVARCHAR(50)  | Specifies if the product requires maintenance (e.g., 'Yes', 'No').                            |
| cost                | INT           | Cost or base price of the product in monetary units.                                          |
| product_line        | NVARCHAR(50)  | Specific product line or series to which the product belongs (e.g., Road, Mountain).          |
| start_date          | DATE          | Date when the product was first available for sale.                                           |

---

### 3. **gold.fact_sales**
- **Purpose:** Captures sales transaction data for analysis.
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | Unique alphanumeric code for each sales order (e.g., 'SO54496').                              |
| product_key     | INT           | Links the sale to a specific product in the product dimension table.                          |
| customer_key    | INT           | Connects the sale to a specific customer in the customer dimension table.                     |
| order_date      | DATE          | Date when the sale order was placed.                                                          |
| shipping_date   | DATE          | Date when the sale order was shipped.                                                         |
| due_date        | DATE          | Expected payment date for the order.                                                          |
| sales_amount    | INT           | Total monetary value of the sale in whole currency units.                                     |
| quantity        | INT           | Number of product units ordered.                                                              |
| price           | INT           | Unit price of the product in whole currency units.                                            |
