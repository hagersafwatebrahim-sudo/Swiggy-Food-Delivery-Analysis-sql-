# Swiggy Sales Analysis Engine 🚴‍♂️🍲

## 📌 Project Overview
This project aims to build a robust, scalable, and performance-optimized Data Warehouse solution using Swiggy's food delivery dataset. The end-to-end engine focuses on transforming messy, raw transactional data into structured, actionable business insights. It covers everything from rigorous Data Cleaning & Validation to creating an optimized Star Schema (Dimensional Modelling), and finally computing core business KPIs to drive strategic decisions.

---

## 🛠️ Phase 1: Data Cleaning & Validation
To ensure absolute data quality and prevent inaccurate metrics, the raw swiggy_data table underwent a strict validation pipeline:

* Null Value Auditing: Inspected critical operational fields (State, City, Order_Date, Restaurant_Name, Location, Category, Dish_Name, Price_INR, Rating, Rating_Count) to isolate missing records.
* Blank/Empty String Check: Detected and handled fields containing empty whitespace that could skew text aggregations.
* Duplicate Detection & Removal: Grouped data across business-critical columns and utilized the window function ROW_NUMBER() to eliminate surplus duplicate rows, retaining exactly one clean copy per unique order.

---

## 📐 Phase 2: Dimensional Modelling (Star Schema)
To optimize analytics, minimize data duplication, and support fast reporting speeds, the flat dataset was decoupled into a highly efficient Star Schema. This design avoids scanning bulky datasets and ensures seamless BI dashboard integration.

### Architecture Overview
* Central Fact Table:
  * fact_swiggy_orders: Contains quantitative metrics (Price_INR, Rating, Rating_Count) and foreign keys linking to all dimension tables.
* Dimension Tables:
  * dim_date: Temporal attributes (Year, Month, Quarter, Week, Day).
  * dim_location: Geographic breakdown (State, City, Location).
  * dim_restaurant: Restaurant_Name.
  * dim_category: Cuisine classification (Category/Cuisine).
  * dim_dish: Distinct food items (Dish_Name).

### Entity-Relationship Diagram (ERD)
*(Tip: Place your ERD image in a folder named images inside your repository and link it here)*
