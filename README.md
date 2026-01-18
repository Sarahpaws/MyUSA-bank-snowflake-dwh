# MyUSA-bank-snowflake-dwh
A snowflake-schema data warehouse in MYSQL for daily bank financial KPIs including NIM,ROA,ROE and efficiency analysis.

# Dataset Source
Kaggle – USA Bank Financial Data
https://www.kaggle.com/datasets/vishalsinghsangral/usa-bank-financial-data
This dataset contains daily financial performance data for a U.S. bank, including income, expenses, assets, equity, market share, and stock prices. The project applies a Snowflake Schema–based data warehouse design supported by an Enhanced Entity Relationship (EER) diagram to model relationships and enforce data integrity.

# Project Overview
The SQL queries executed on this database provide in-depth insights into bank profitability, operational efficiency, asset utilization, and market performance over time.
The project follows a Snowflake Schema design, where time dimensions are normalized into hierarchical tables, and the logical structure is documented using an EER diagram for clarity and correctness.

# 1. Data Overview & Initial Validation
Explored the raw dataset (myusabank) to understand data volume, schema, and reporting period.
Validated minimum and maximum dates to ensure complete time-series coverage.
Identified duplicate records at the daily level and resolved them through aggregation.
Performed integrity checks before dimensional modeling and fact loading.

# 2. EER Diagram & Data Modeling Design
An Enhanced Entity Relationship (EER) diagram was created to visually represent:
Entity structures (dimensions and fact table)
Primary and foreign key relationships
Hierarchical dependencies within the time dimension
Cardinality and referential integrity constraints
The EER diagram ensures that the logical data model accurately reflects the Snowflake Schema architecture implemented in SQL and serves as a blueprint for the physical database design.

# 3. Snowflake Schema Design
The database follows a Snowflake Schema, particularly for the time dimension, resulting in reduced redundancy and improved data consistency.
Dimension Tables:
DIM_BANK – Stores bank-level master information.
DIM_YEAR – Year-level attributes.
DIM_QUARTER – Linked to year for quarterly analysis.
DIM_MONTH – Linked to quarter and year for monthly analysis.
DIM_DATE – Linked to month, containing detailed calendar attributes.
Fact Table: FACT_BANK_DAILY_FINANCE – Captures daily financial measures and references normalized dimensions using foreign keys.

# 4. Financial Measures & KPI Analysis
Using the snowflake dimensions and fact table, multiple banking KPIs were computed.
Base Measures:
Interest Income
Interest Expense
Net Income
Total Assets
Shareholder Equity
Operating Income
Operating Expenses
Market Share
Stock Price
Derived KPIs:
Net Interest Income (NII)
Net Interest Margin (NIM)
Return on Assets (ROA)
Return on Equity (ROE)
Efficiency Ratio
Equity Ratio
All ratio calculations were implemented using NULL-safe logic to ensure accuracy.

# 5. Time-Series & Trend Analysis
Monthly and yearly profit trends using normalized time dimensions.
Net interest income movement across months and years.
Efficiency ratio trends to evaluate cost control.
ROA and ROE trends to assess financial performance.
Identification of top-performing months based on profitability.

# 6. Analytical View Layer
A reusable analytical view (v_bank_daily_kpis) was created to:
Join fact and dimension tables defined in the EER model.
Centralize KPI calculations.
Simplify analytical queries and reporting.
Support BI and dashboarding tools.

# 7. Data Quality & Consistency Checks
Duplicate date entries handled via aggregation before fact loading.
Referential integrity enforced through primary and foreign key constraints.
Division-by-zero errors prevented using NULLIF.
Fact table reloads performed to maintain clean and consistent data.

# Dataset Columns – Description
Each column represents a daily financial indicator used in the analytical model.
Date – Financial reporting date
Interest_Income – Income generated from interest-bearing assets
Interest_Expense – Cost of funds
Average_Earning_Assets – Assets generating interest
Net_Income – Net profit
Total_Assets – Total assets held by the bank
Shareholder_Equity – Owners’ equity
Operating_Income – Core operational income
Operating_Expenses – Operational costs
Market_Share – Market presence indicator
Stock_Price – Daily stock price

# How to Run the Project
# Step 1: Clone or Download the Repository
Clone this repository using Git or download it as a ZIP file.
# Step 2: Set Up the Database Environment
Install MySQL 8.0 or higher.
Create a new connection in MySQL Workbench.
# Step 3: Import the Dataset
Download the dataset from Kaggle.
Import the CSV file into a staging table named myusabank.
# Step 4: Execute the SQL Script
Run the SQL script sequentially to:
Create the database and tables
Implement the EER-based snowflake schema
Populate dimension tables
Load the fact table
Create analytical views
Execute KPI and trend analysis queries
# Step 5: Review & Analyze Results
Validate row counts and key relationships.
Query v_bank_daily_kpis for insights.
Analyze trends across days, months, quarters, and years.

# Summary
This project demonstrates end-to-end financial analytics using SQL, supported by a Snowflake Schema and an EER diagram. By normalizing time dimensions and enforcing relational integrity, the project enables reliable, scalable, and insightful analysis of banking performance.
It highlights expertise in:
EER diagram design
Snowflake schema modeling
Financial KPI computation
Time-series analysis
Data quality validation
Advanced SQL querying
This project is well-suited for Finance Analyst, Data Analyst, and Business Intelligence roles.
