# 🚑 San Francisco Emergency Response Dashboard (Power BI)

### 📊 Project Overview
This project is a comprehensive Business Intelligence solution designed to analyze emergency dispatch performance. Using **San Francisco Fire & EMS open data**, it simulates a real-world operational dashboard for a 911 center (similar to E-Comm 911).

**🚀 Quick Access:**
* [**👉 View Live Interactive Dashboard**](https://app.powerbi.com/links/2k8PmfR3YT?ctid=8322cefd-0a4c-4e2c-bde5-b17933e7b00f&pbi_source=linkShare) *(Best for viewing visuals)*
* [**📂 Download .pbix Source File**](https://drive.google.com/file/d/1MmV1hip2efcc5mXpUCVW0X9TgG5cG44J/view?usp=sharing) *(Hosted on Drive due to 300MB file size)*
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

#### 1. Robust Data Engineering (ETL & Power Query)
* **Dynamic Date Dimension:** Engineered a flexible Date Table using M Code that automatically adjusts its end date based on the latest Fact Table data, resolving "future date" slicer issues.
* **Data Cleansing Logic:** Implemented defensive Power Query formulas to sanitize raw 9-1-1 data, specifically handling negative duration anomalies and null values to prevent skewed KPI calculations.
* **Lifecycle Metrics Calculation:** Calculated 5 distinct timestamp metrics (Processing, Turnout, Travel, Response, Scene Duration) directly in the ETL layer to optimize report performance.
  
#### 2. Advanced DAX & Analytics
* **Context Manipulation:** Utilized CALCULATE with REMOVEFILTERS to Engineer precise Time Intelligence measures (e.g., YoY % Change), solving complex filter interaction issues caused by month-level slicers.

#### 3. UX & Interactivity
* **Diagnostic Drill-through:** Designed a deep-dive "Operational Analysis" page that allows users to seamlessly transition from high-level neighborhood trends to row-level incident details.

---

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
