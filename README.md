🌟 SECTION 1: Data Warehousing
Task 1 — Star Schema Design

We designed a star schema to organize retail sales information into a format suitable for analytical queries.

📌 Fact Table: SalesFact
Contains numerical measures:

| SalesID | ProductID | CustomerID | DateID | Quantity | UnitPrice | TotalSales |

📌 Dimension Tables:

CustomerDim	ProductDim	TimeDim
CustomerID, Country	ProductID, ProductName	DateID, Date, Month, Quarter, Year

Why Star Schema?
Star schema is chosen for speed, simplicity, and efficient OLAP analysis.
It reduces join complexity and supports drill-down/roll-up queries.

📍 Diagram included: images/star_schema_diagram.png

Task 2 — ETL Process (Retail Warehouse Build)

Script: scripts/etl_retail.py

✔ Extracted dataset from Excel
✔ Cleaned data (removed refunds, null CustomerID, negative values)
✔ Created new metrics like TotalSales
✔ Loaded data into SQLite warehouse retail_dw.db

Run using:

python scripts/etl_retail.py

Task 3 — OLAP Queries & Business Insights

Script: scripts/olap_queries.py

Queries performed:

Query	Type	Example Insight
Total sales by country quarterly	Roll-Up	UK was highest revenue generator
Monthly sales for a specific country	Drill-Down	Seasonal trend visible around December
Sales filtered by Category/StockCode	Slice	Certain items peak during holidays

Run:

python scripts/olap_queries.py


📊 Visual Sample: stored as images/sales_by_country.png

🧠 SECTION 2: Data Mining & Machine Learning
Task 1 — Data Preprocessing & Exploration

Script: scripts/preprocessing_iris.py

Performed operations:

Checked missing values

Min-Max normalization

Pair plots, heatmap, boxplots

Train/Test split (80/20)

📈 Visual outputs included in /images/

Task 2 — Clustering (KMeans)

Script: scripts/clustering_iris.py

Applied KMeans with k = 3

Evaluated performance using Adjusted Rand Index (ARI)

Generated Elbow Curve to justify optimal K

Results:

k	ARI Score
3	~0.73 (good clustering alignment)
Task 3 — Classification & Association Rule Mining

Script: scripts/mining_iris_basket.py

🔹 Classification Models
Model	Accuracy	Notes
Decision Tree	~95%	Interpretable features
KNN (k=5)	~92%	Slightly lower but stable

Decision Tree visualization saved as:

📁 images/decision_tree_viz.png

🔹 Association Rule Mining (Apriori)

Synthetic shopping basket transactions generated

Rules mined using MLxtend

Output example:

Rule	Confidence	Lift
{Diapers} → {Beer}	0.67	1.5

Useful for supermarket layouts & product recommendations.

📌 Summary & Conclusion

This project demonstrates the complete lifecycle of data handling:

Stage	Tools Used	Outcome
Storage	SQLite	Retail Data Warehouse
ETL	Python + Pandas	Cleaned transaction data
OLAP	SQL queries	Business insights
ML	Scikit-Learn	Predictive & descriptive analytics
Rules	Apriori	Consumer behavior insights

We successfully connected data engineering + data mining, proving how raw data evolves into actionable knowledge.

📎 Future Improvements

If extended further, the system could include:

Automated monthly ETL job scheduling

Dashboard using PowerBI/Streamlit

Customer segmentation model on retail data

Real-time sales forecasting using ARIMA/LSTM

🏁 Final Note

This work is original, developed for DSA 2040 Practical Exam and demonstrates applied understanding of:

✔ Warehousing
✔ ETL
✔ OLAP
✔ Machine Learning
✔ Pattern Mining
