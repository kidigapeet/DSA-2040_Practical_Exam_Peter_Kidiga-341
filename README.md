🏬 DSA 2040 Practical Exam — Data Warehousing & Data Mining Project








Student Name: Peter Kidiga
Student ID: 341
Course: DSA 2040 — Data Warehousing & Data Mining (FS 2025)
Submission Date: 10/12/2025

📌 Project Overview

This project demonstrates end-to-end applied data science, combining:

<details> <summary>1️⃣ Data Warehousing</summary>

Designed, cleaned, transformed, and stored a large retail dataset from UCI Online Retail II

Implemented a warehouse structure for analytical queries

Executed OLAP queries for insights: sales trends across time, products, and regions

</details> <details> <summary>2️⃣ Data Mining</summary>

Used Iris dataset to extract patterns:

Clustering (K-Means) — group similar data points

Classification (Decision Tree & KNN) — predict flower species

Association Rule Mining (Apriori) — analyze market basket behavior

</details>

This project bridges data engineering (ETL + warehousing) with data science (modeling + pattern mining).

📁 Repository Structure
DSA2040_Practical_Exam_PeterKidiga_341/
│
├── data/
├── scripts/
├── outputs/
├── images/
└── README.md

🔧 Setup & Installation
pip install pandas numpy scikit-learn matplotlib seaborn mlxtend sqlite3 openpyxl


Dataset: Download Online Retail II from UCI and save as:

data/Online Retail.xlsx

🌟 SECTION 1: Data Warehousing
<details> <summary>⭐ Star Schema Design</summary>

Fact Table: SalesFact

Column	Description
SalesID	Unique transaction ID
ProductID	Product identifier
CustomerID	Customer identifier
DateID	Date reference
Quantity	Units sold
UnitPrice	Price per unit
TotalSales	Quantity × UnitPrice

Dimension Tables:

CustomerDim	ProductDim	TimeDim
CustomerID, Country	ProductID, ProductName	DateID, Date, Month, Quarter, Year

📌 Diagram: images/star_schema_diagram.png

Why Star Schema?

Fast, simple, OLAP-friendly

Reduces joins

Supports drill-down/roll-up

</details> <details> <summary>⭐ ETL Process</summary>

Script: scripts/etl_retail.py

✅ Steps:

Extract Excel dataset

Clean data (remove refunds, null CustomerID, negative values)

Create TotalSales metric

Load into SQLite warehouse (retail_dw.db)

Run:

python scripts/etl_retail.py

</details> <details> <summary>⭐ OLAP Queries & Insights</summary>

Script: scripts/olap_queries.py

Query Type	Example Insight
Total sales by country quarterly (Roll-Up)	UK highest revenue
Monthly sales for a specific country (Drill-Down)	December seasonal spike
Sales filtered by category/stock (Slice)	Certain items peak during holidays

📊 Sample Visualization: images/sales_by_country.png

Run:

python scripts/olap_queries.py

</details>
🧠 SECTION 2: Data Mining & Machine Learning
<details> <summary>⭐ Data Preprocessing & EDA</summary>

Script: scripts/preprocessing_iris.py

✅ Steps:

Check missing values

Min-Max normalization

Pair plots, heatmaps, boxplots

Train/Test split (80/20)

Visual outputs: /images/

</details> <details> <summary>⭐ Clustering (K-Means)</summary>

Script: scripts/clustering_iris.py

KMeans k = 3

Adjusted Rand Index (ARI) evaluation

k	ARI Score
3	~0.73 ✅

Elbow Curve: images/elbow_curve.png

Cluster Visualization: images/cluster_visualization.png

</details> <details> <summary>⭐ Classification & Association Rule Mining</summary>

Script: scripts/mining_iris_basket.py

Classification Models

Model	Accuracy	Notes
Decision Tree	~95%	Interpretable features
KNN (k=5)	~92%	Stable performance

Decision Tree visualization: images/decision_tree_viz.png

Association Rule Mining (Apriori)

Rule	Confidence	Lift
{Diapers} → {Beer}	0.67	1.5
</details>
📌 Summary & Conclusion
Stage	Tools Used	Outcome
Storage	SQLite	Retail Data Warehouse
ETL	Python + Pandas	Cleaned transaction data
OLAP	SQL queries	Business insights
ML	Scikit-Learn	Predictive & descriptive analytics
Rules	Apriori	Consumer behavior insights

✅ Demonstrates full data lifecycle: raw data → actionable knowledge.

📎 Future Improvements

Automated monthly ETL jobs

Dashboard (PowerBI / Streamlit)

Customer segmentation model

Real-time sales forecasting (ARIMA/LSTM)
