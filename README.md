# 🍔 Swiggy-Order-Revenue-Analytics

An end-to-end SQL data analytics project analyzing 197,430+ food delivery transactions across India to uncover ordering patterns, restaurant performance, and customer spending behavior through dimensional modeling and comprehensive KPI tracking.

## 📊 Project Overview

This project transforms raw Swiggy delivery data into actionable business insights using pure SQL for data warehousing, star schema modeling, and comprehensive analytics. All data cleaning, transformation, and analysis performed entirely in SQL.

## 🎯 Key Features

- **Data Quality Assurance**: Comprehensive validation, duplicate detection, and cleansing
- **Star Schema Implementation**: Optimized dimensional model for efficient analytics
- **KPI Dashboard**: Core metrics tracking orders, revenue, ratings, and pricing
- **Multi-Dimensional Analysis**: Deep-dive into temporal, geographic, and product performance
- **Customer Segmentation**: Spending behavior analysis across price buckets

## 🗂️ Dataset Summary

- **Records**: 197,430 food delivery transactions
- **Columns**: 10 attributes
- **Key Fields**:
  - **Location Data**: State, City, Location
  - **Restaurant Info**: Restaurant Name, Category
  - **Product Details**: Dish Name, Price (INR)
  - **Customer Feedback**: Rating (1-5), Rating Count
  - **Temporal Data**: Order Date

## 🛠️ Tech Stack

- **SQL**: Complete end-to-end implementation using pure SQL
- **Database**: PostgreSQL/MySQL for data warehousing
- **Star Schema Design**: Dimensional modeling for optimized queries

## 🔍 Analysis Workflow

### 1. Data Cleaning & Validation
**Quality Checks Performed:**
- **Null Detection**: Identified missing values across all critical fields
- **Blank String Validation**: Detected empty strings in key columns
- **Duplicate Detection**: Found redundant records using grouped analysis
- **Duplicate Removal**: Applied ROW_NUMBER() to retain unique orders only

**Validated Fields:**
- State, City, Order Date
- Restaurant Name, Location
- Category, Dish Name
- Price (INR), Rating, Rating Count

### 2. Dimensional Modeling (Star Schema)
Built optimized data warehouse structure for scalable analytics:

#### Dimension Tables
- **dim_date**: Year, Month, Quarter, Week (extracted from Order Date)
- **dim_location**: State, City, Location hierarchy
- **dim_restaurant**: Restaurant Name and attributes
- **dim_category**: Category/Cuisine classifications
- **dim_dish**: Dish Name and details

#### Fact Table
- **fact_swiggy_orders**: Central table containing:
  - Measures: Price (INR), Rating, Rating Count
  - Foreign keys linking to all dimension tables

**Benefits:**
- Eliminates data redundancy
- Accelerates query performance
- Simplifies BI tool integration
- Enables efficient aggregations

### 3. KPI Development
**Core Business Metrics:**
- Total Orders
- Total Revenue (INR Million)
- Average Dish Price
- Average Rating

### 4. Deep-Dive Business Analysis

#### Date-Based Analysis
- Monthly order trends and seasonality
- Quarterly performance comparison
- Year-over-year growth patterns
- Day-of-week ordering behavior

#### Location-Based Insights
- Top 10 cities by order volume
- State-wise revenue contribution
- Geographic expansion opportunities

#### Food Performance Metrics
- Top 10 restaurants by order count
- Category performance (Indian, Chinese, Continental, etc.)
- Most ordered dishes across platform
- Cuisine analysis with ratings correlation

#### Customer Spending Analysis
**Price Bucket Segmentation:**
- Under ₹100
- ₹100-199
- ₹200-299
- ₹300-499
- ₹500+

Order distribution and customer behavior per segment.

#### Ratings Distribution
Analysis of dish ratings from 1-5 stars to identify quality patterns.

## 💡 Key Insights & Recommendations

### Business Strategies
1. **Restaurant Partnerships**: Focus on high-performing restaurants and cuisines
2. **Geographic Expansion**: Prioritize underserved high-potential cities
3. **Pricing Optimization**: Leverage spending bucket insights for promotions
4. **Quality Assurance**: Address low-rated dishes and restaurants
5. **Temporal Marketing**: Target campaigns during peak ordering periods

## 📁 Repository Structure

```
├── data/
│   ├── raw/                    # Original Swiggy dataset
│   └── cleaned/                # Validated data
├── sql/
│   ├── 01_data_cleaning.sql    # Validation & cleansing
│   ├── 02_star_schema.sql      # Dimensional model creation
│   ├── 03_kpi_queries.sql      # Business metrics
│   └── 04_analysis_queries.sql # Deep-dive analytics
├── schema/
│   └── erd_diagram.png         # Star schema visualization
├── reports/
│   └── business_analysis.pdf   # Detailed findings
└── README.md
```

## 🚀 Getting Started

### Prerequisites
```bash
PostgreSQL 12+ / MySQL 8.0+
SQL Client (pgAdmin, DBeaver, MySQL Workbench, or any SQL editor)
```

### Installation
```bash
# Clone repository
git clone https://github.com/yourusername/swiggy-sales-analysis.git

# Set up database
psql -U postgres -c "CREATE DATABASE swiggy_analytics;"

# Run schema creation
psql -U postgres -d swiggy_analytics -f sql/02_star_schema.sql

# Load and clean data
psql -U postgres -d swiggy_analytics -f sql/01_data_cleaning.sql
```

### Usage
```bash
# Execute KPI calculations
psql -U postgres -d swiggy_analytics -f sql/03_kpi_queries.sql

# Run business analysis queries
psql -U postgres -d swiggy_analytics -f sql/04_analysis_queries.sql
```

## 📈 Results

- Built complete data warehouse using **pure SQL** implementation
- Established 5-table star schema for optimized reporting
- Calculated platform-wide KPIs for executive dashboards
- Identified top revenue-generating cities and restaurants
- Mapped customer spending patterns across price segments
- Analyzed temporal ordering trends for marketing optimization

## 🏗️ Star Schema Architecture

The project implements a robust dimensional model with:
- **5 dimension tables** for descriptive attributes
- **1 central fact table** for measurable metrics
- **Referential integrity** through foreign key relationships
- **Performance optimization** via indexed dimension keys

This architecture enables:
- Fast query execution for complex analytics
- Easy dashboard integration with BI tools
- Scalable data structure for growing datasets
- Simplified maintenance and updates
