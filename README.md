# 🚑 San Francisco Emergency Response Dashboard (Power BI)

### 📊 Project Overview
This project is a comprehensive Business Intelligence solution designed to analyze emergency dispatch performance. Using **San Francisco Fire & EMS open data**, it simulates a real-world operational dashboard for a 911 center (similar to E-Comm 911).

**🚀 Quick Access:**
* [**👉 View Live Interactive Dashboard**](https://app.powerbi.com/links/2k8PmfR3YT?ctid=8322cefd-0a4c-4e2c-bde5-b17933e7b00f&pbi_source=linkShare) *(Best for viewing visuals)*
* [**📂 Download .pbix Source File**](https://drive.google.com/file/d/1H-dLFQVHeCoH5U_2R1KybBpTa0uoMbhT/view) *(Hosted on Drive due to 300MB file size)*
---

### 📷 Dashboard Preview

**1. Executive Overview**
*High-level view of Call Volumes and Average Response Times.*
![Overview](overview.png)

**2. Operational Details**
*Drill-through analysis of incident types and unit performance.*
![Details](details.png)

**3. Data Model (Star Schema)**
*Optimized schema with dedicated Date Dimension.*
![Data Model](model.png)

---

### 🛠️ Technical Highlights

#### 1. Advanced Data Modeling
* Engineered a robust **Star Schema** to optimize query performance for millions of dispatch records.
* Created a dedicated **Date Dimension** using M Code (Power Query) to enable Time Intelligence functions.

#### 2. Complex DAX Calculations
* **Response Time Analysis:** Calculated weighted averages for critical KPI tracking.
* **Time Intelligence:** Implemented `CALCULATE` and `USERELATIONSHIP` to analyze data by both "Received Date" and "Dispatch Date".

#### 3. UX & Interactivity
* Designed **Drill-through** functionality to allow users to navigate from high-level trends to granular incident details.
* Implemented dynamic filtering for different Unit Types (Engine, Truck, Medic).

---

### 🧹 Data Transformation & Quality Logic
To ensure the accuracy of operational metrics, the following cleaning rules and logic were applied:
* **🚫 Handling Anomalies (Negative Values):**
    * Excluded records where *Scene Duration* or *Response Time* resulted in negative values (typically caused by manual entry errors or system sync issues).
* **⚠️ Null Handling:**
    * Implemented DAX logic (using `ISNOTBLANK`) to calculate averages only when both *Start* and *End* timestamps are valid, preventing skewed KPI results.
* **📅 Dynamic Date Dimension:**
    * Created a continuous `Dim_Date` table using M Code to support Time Intelligence functions (YoY, MoM analysis).
    * **Range:** Covers the full dataset period from **Jan 2018 to Feb 2026**.

### 📂 Data Source
* **Source:** [San Francisco Fire Department Calls for Service] - https://data.sfgov.org/Public-Safety/Fire-Department-and-Emergency-Medical-Services-Dis/nuek-vuh3/about_data
* **Dataset:** Includes Call Number, Unit ID, Call Type, Received DtTm, Dispatch DtTm, and On Scene DtTm.

### 📂 Data Documentation
* **Source Dictionary:** [👉 View Original Data Dictionary](./DataDictionary.xlsx)
    *(Official definitions for raw columns provided by SF Open Data)*

* **Key Calculated Metrics (My Logic):**
    * Call Processing Time: Dispatch_DtTm - Received_DtTm
    * Turnout Time: Response_DtTm - Dispatch_DtTm
    * Travel Time: On_Scene_DtTm - Response_DtTm
    * Total Response Time: On_Scene_DtTm - Received_DtTm
    * Scene Duration: Available_DtTm - On_Scene_DtTm

* **KPI Targets (SLA Benchmarks):**
    * High Priority: Response within 10 Minutes.
    * Medium Priority: Response within 15 Minutes.
    * Low Priority: Response within 20 Minutes.

### 📬 Contact
* **Jill Lau**
* LinkedIn: [Jill Lau](https://www.linkedin.com/in/jill-data)
