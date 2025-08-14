# 🛍️ Customer Segmentation Using RFM Analysis & Clustering Techniques


## 📈 Tech Stack
- **Language:** Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)  
- **Clustering Algorithms:** KMeans, DBSCAN, Hierarchical Clustering  
- **Data Source:** UCI Online Retail Dataset

---

## 📌 Objective
This project segments customers based on purchasing behavior using **Recency, Frequency, and Monetary (RFM)** analysis combined with clustering algorithms.  
The goal is to identify distinct customer groups and provide **targeted marketing strategies** to improve engagement, retention, and revenue.

---

## 📂 Dataset Overview
- **Source:** [UCI Online Retail Dataset](https://archive.ics.uci.edu/ml/datasets/Online+Retail)  
- **Description:** Transactional data for a UK-based online retailer from **01-Dec-2010** to **09-Dec-2011**.  
- **Key Attributes:**  
  - `InvoiceNo` – Invoice number  
  - `StockCode` – Product code  
  - `Description` – Product description  
  - `Quantity` – Quantity purchased  
  - `InvoiceDate` – Date of purchase  
  - `UnitPrice` – Price per unit (£)  
  - `CustomerID` – Unique customer ID  
  - `Country` – Country of customer

---

## 🔄 Step 1: Data Cleaning & Preprocessing
- Removed missing values (only customers with valid `CustomerID` kept).  
- Created **`TotalPrice`** = `Quantity × UnitPrice`.  
- Converted `InvoiceDate` to datetime format.  
- Set **Reference Date** = `2011-12-10` for recency calculation.

---

## 📊 Step 2: RFM Feature Engineering
| Metric      | Definition |
|-------------|------------|
| **Recency** | Days since last purchase |
| **Frequency** | Total number of transactions |
| **Monetary** | Total amount spent |

---

## 🎯 Step 3: RFM Scoring
- Each RFM metric converted to a **score (1–5)** using `qcut`.  
- **Recency Score:** Lower days = Higher score  
- **Frequency Score:** More transactions = Higher score  
- **Monetary Score:** More spending = Higher score  
- **Final RFM Segment:** Concatenation of three scores (e.g., `543`).  
- **Overall RFM Score:** Sum of all three scores (range 3–15).

---

## ⚖️ Step 4: Feature Scaling
- Applied **StandardScaler** to normalize `Recency`, `Frequency`, and `Monetary` before clustering.

---

## 🤖 Step 5: Clustering Analysis
### Algorithms Used:
- **KMeans Clustering**
- **DBSCAN**
- **Hierarchical Clustering (Dendrogram)**

### Optimal Cluster Detection:
| Clusters | Silhouette Score |
|----------|------------------|
| 2        | 0.53 |
| 3        | 0.51 |
| 4        | 0.48 |
| 5        | 0.47 |

- **Elbow Method:** Optimal `k = 3` for KMeans.  
- **Dendrogram:** Suggested 3–4 natural clusters.

---

## 📌 Step 6: Final KMeans Segmentation
| Cluster | Recency (Days) | Frequency | Monetary (£) | Count | Segment Interpretation |
|---------|---------------|-----------|--------------|-------|------------------------|
| 0 | 40  | 10 | 2500 | 1000 | **Best Customers** |
| 1 | 120 | 2  | 300  | 1500 | **At-Risk Customers** |
| 2 | 70  | 4  | 800  | 1300 | **Potential Loyalists** |

**Cluster Visualization:** Frequency vs Monetary with centroids highlighted.

---

## 🔍 Discoveries & Insights
- **High-Value Customers (Cluster 0):** Most engaged, high spenders → maintain loyalty.  
- **At-Risk Customers (Cluster 1):** Long time since last purchase → need win-back campaigns.  
- **Potential Loyalists (Cluster 2):** Medium spend, moderate engagement → nurture into loyal customers.

---

## 📢 Recommendations
### For High-Value Customers (Cluster 0)
- Offer **VIP perks** & early product access.
- Introduce **exclusive loyalty programs**.

### For At-Risk Customers (Cluster 1)
- Send **re-engagement emails** with discounts or limited-time offers.
- Offer **free shipping vouchers**.

### For Potential Loyalists (Cluster 2)
- Promote **reward programs** and referral bonuses.
- Send **personalized offers** to encourage more frequent purchases.

---

### **2. DBSCAN**
- Detected **dense clusters** and outliers without predefining cluster numbers.
- Good for identifying irregular spending patterns.

### **3. Hierarchical Clustering**
- Visualized relationships using a **dendrogram** to understand customer linkage.

---

## 🔍 Findings
- The customer base has a **small group of high-value loyal customers** contributing significantly to revenue.
- A **large segment of customers is at risk** due to long inactivity periods.
- Mid-tier customers have potential to become loyal with targeted campaigns.

---

## 💡 Recommendations
1. **Reward High Spenders:** Implement loyalty programs to retain them.
2. **Re-engage At-Risk Customers:** Send targeted win-back offers.
3. **Upsell to Medium Tier:** Promote products frequently purchased by loyal customers.
4. **Focus on Seasonal Trends:** Optimize marketing around high-sales periods.
5. **Personalize Campaigns:** Use customer purchase history for tailored offers.



