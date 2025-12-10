# 🏬 DSA 2040 Practical Exam — Data Warehousing & Data Mining Project

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)  
![SQLite](https://img.shields.io/badge/SQLite-3.40-003B57?logo=sqlite&logoColor=white)  
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.25-orange?logo=scikit-learn&logoColor=white)  
![MLxtend](https://img.shields.io/badge/MLxtend-0.20-green)  

**Student Name:** Peter Kidiga  
**Student ID:** 341  
**Course:** DSA 2040 — Data Warehousing & Data Mining (FS 2025)  
**Submission Date:** 10/12/2025  

---

## 📌 Project Overview

This project demonstrates **end-to-end applied data science**, combining:  

<summary>1️⃣ Data Warehousing</summary>

- Designed, cleaned, transformed, and stored a **large retail dataset** from UCI Online Retail II  
- Implemented a **warehouse structure** for analytical queries  
- Executed **OLAP queries** for insights: sales trends across time, products, and regions  


2️⃣ Data Mining</summary>

- Used **Iris dataset** to extract patterns:  
  - **Clustering (K-Means)** — group similar data points  
  - **Classification (Decision Tree & KNN)** — predict flower species  
  - **Association Rule Mining (Apriori)** — analyze market basket behavior  



This project bridges **data engineering (ETL + warehousing)** with **data science (modeling + pattern mining)**.

---

## 📁 Repository Structure

```
DSA2040_Practical_Exam_PeterKidiga_341/
│
├── data/
├── scripts/
├── outputs/
├── images/
└── README.md
```

---

## 🔧 Setup & Installation

```bash
pip install pandas numpy scikit-learn matplotlib seaborn mlxtend sqlite3 openpyxl
```

**Dataset:** Download Online Retail II from UCI and save as:

```
data/Online Retail.xlsx
```

---

## 🌟 SECTION 1: Data Warehousing


<summary>⭐ Star Schema Design</summary>

**Fact Table:** `SalesFact`  

| Column      | Description            |
|------------|------------------------|
| SalesID    | Unique transaction ID  |
| ProductID  | Product identifier     |
| CustomerID | Customer identifier    |
| DateID     | Date reference         |
| Quantity   | Units sold             |
| UnitPrice  | Price per unit         |
| TotalSales | Quantity × UnitPrice   |

**Dimension Tables:**  

| CustomerDim      | ProductDim          | TimeDim                   |
|-----------------|------------------|---------------------------|
| CustomerID, Country | ProductID, ProductName | DateID, Date, Month, Quarter, Year |

📌 Diagram: `images/star_schema_diagram.png`  
<img width="1000" height="800" alt="Star_schema_diagram" src="https://github.com/user-attachments/assets/4e96918a-8680-4661-b83b-0099b32eb90b" />

*Why Star Schema?*  
- Fast, simple, OLAP-friendly  
- Reduces joins  
- Supports drill-down/roll-up  


**Script:** `scripts/etl_retail.py`  

✅ Steps:  
- Extract Excel dataset  
- Clean data (remove refunds, null CustomerID, negative values)  
- Create `TotalSales` metric  
- Load into SQLite warehouse (`retail_dw.db`)  

**Run:**  
```bash
python scripts/etl_retail.py
```


**Script:** `scripts/olap_queries.py`  

| Query Type                    | Example Insight |
|--------------------------------|----------------|
| Total sales by country quarterly (Roll-Up) | UK highest revenue |
| Monthly sales for a specific country (Drill-Down) | December seasonal spike |
| Sales filtered by category/stock (Slice) | Certain items peak during holidays |

📊 Sample Visualization: 

<img width="846" height="547" alt="montlysalesTrend_UK" src="https://github.com/user-attachments/assets/2de9784b-87e2-425f-ba0f-0d9ef3021ed5" />

**Run:**  
```bash
python scripts/olap_queries.py
```



---

## 🧠 SECTION 2: Data Mining & Machine Learning


**Script:** `scripts/preprocessing_iris.py`  

✅ Steps:  
- Check missing values  
- Min-Max normalization  
- Pair plots, heatmaps, boxplots  
- Train/Test split (80/20)  

**Visual outputs:** `/images/`


<img width="693" height="547" alt="K_means_cluster" src="https://github.com/user-attachments/assets/76fe99dd-af9a-4f0f-b0c4-9bc275cebdc0" />

**Script:** `scripts/clustering_iris.py`  

- KMeans **k = 3**  
- Adjusted Rand Index (ARI) evaluation  

| k | ARI Score |
|---|-----------|
| 3 | ~0.73 ✅ |

- Elbow Curve: `images/elbow_curve.png`  
- Cluster Visualization: `images/cluster_visualization.png`  



**Script:** `scripts/mining_iris_basket.py`  

**Classification Models**

| Model         | Accuracy | Notes                  |
|---------------|---------|-----------------------|
| Decision Tree | ~95%    | Interpretable features |
| KNN (k=5)     | ~92%    | Stable performance    |

Decision Tree visualization: `images/decision_tree_viz.png`  

<img width="950" height="658" alt="Decision_tree_vz" src="https://github.com/user-attachments/assets/7acdbe11-2254-4b7e-89ee-b6ac9897e71d" />

**Association Rule Mining (Apriori)**

| Rule                 | Confidence | Lift |
|----------------------|-----------|------|
| {Diapers} → {Beer}   | 0.67      | 1.5  |



---

## 📌 Summary & Conclusion

| Stage       | Tools Used           | Outcome                           |
|------------|--------------------|----------------------------------|
| Storage    | SQLite             | Retail Data Warehouse             |
| ETL        | Python + Pandas     | Cleaned transaction data          |
| OLAP       | SQL queries         | Business insights                 |
| ML         | Scikit-Learn        | Predictive & descriptive analytics |
| Rules      | Apriori             | Consumer behavior insights        |

✅ Demonstrates **full data lifecycle: raw data → actionable knowledge**.

---

## 📎 Future Improvements
- Automated monthly ETL jobs  
- Dashboard (PowerBI / Streamlit)  
- Customer segmentation model  
- Real-time sales forecasting (ARIMA/LSTM)  

---

**🏁 Final Note**  
Original work for **DSA 2040 Practical Exam**, showcasing:  
✔ Warehousing | ✔ ETL | ✔ OLAP | ✔ Machine Learning | ✔ Pattern Mining
