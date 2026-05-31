# Pharmaceutical Supply Chain Control Tower: Operations & Fulfillment Intelligence

## 📌 Executive Summary
In the pharmaceutical manufacturing sector, supply chain disruptions aren't just financial issues—they directly impact product availability and patient compliance. This project delivers an enterprise-grade **Supply Chain Control Tower** developed in Power BI. 

By integrating disparate datasets tracking production manufacturing logs and logistics schedules, this solution shifts operations from descriptive reporting to **diagnostic analytics**. It answers not only *what* our metrics are, but down to the exact root cause of *why* we are experiencing production variances.

---

## 🛠️ Tech Stack & Architecture
* **Analytics & Visualization Engine:** Microsoft Power BI Desktop
* **Data Modeling:** Star Schema (1:Many Relationships, Single Directional Filtering)
* **Data Transformation:** Power Query M-Engine (Data Cleaning, Schema Alignment)
* **Analytical Expressions:** Advanced DAX (Data Analysis Expressions)

---

## 📊 Dashboard Architecture & Performance Metrics

The dashboard is laid out in a strict hierarchy optimized for rapid executive consumption:

### 1. The Strategic Pulse (Top KPI Row)
* **Total Volume (814K):** Aggregated physical yield across all manufacturing runs.
* **Fulfillment Rate (100%):** Measures customer service levels and on-time shipment execution.
* **Output Variance (-2,275):** The ultimate measure of manufacturing reliability. Highlights that production fell **2,275 units short** of our planned manufacturing schedule.
* **Stockout Risk:** Real-time flagging of inventory shortfalls to prevent delivery failure.

### 2. Operational & Tactical Diagnostics (Middle & Bottom Sections)
* **Volume Trends Over Time:** A time-series line chart tracking day-by-day volatility in production yield throughout May 2026.
* **Factory Efficiency Gauge:** Tracks current plant utilization sitting at 78%, visualizing room for throughput optimization.
* **Geographic & Drug Status Matrix:** Deep-dive operational table tracking Drug Status across regions (`EU France`, etc.), filtered dynamically by a dedicated custom time slicer.

![Dashboard Overview](https://github.com/SOMTO-2006/Pharma-supply-chain-analytics/blob/main/Pharma%20Dashboard.png)

---

## 🧠 Relational Data Model Schema

To achieve true diagnostic capability, the data architecture relies on a clean **Star Schema** to eliminate redundancy and maximize cross-filtering performance.

* **Fact Tables:** Centralizes operational performance data (`Actual_Volume`, `Planned_Volume`, `Fulfillment`).
* **Dimension Tables:** Includes a decoupled **DateTable** for advanced Time-Intelligence calculations, and standard product dimension mapping.
* **Relationship Integrity:** Configured with strict `1:Many (1:*)` relationships utilizing single-directional filtering to preserve data lineage and prevent double-counting of volumes across intersecting dimensions.

![Data Model Schema](https://github.com/SOMTO-2006/Pharma-supply-chain-analytics/blob/main/Pharma%20Dashboard%20Data%20Model.png)

---

## 💻 Advanced DAX Expressions (Analytical Layer)

The intelligence layer utilizes custom DAX measures built to handle data sparsity and clear calculations without bloating file size.

### Core Calculations Include:
* **Output Variance:** Establishes the exact delta between manufacturing scheduling expectations and absolute floor realities.
* **Zero-Fill Handling:** Implements optimization functions to bypass blank data blocks within sparse matrix rows, replacing visual voids with structural `0` markers to ensure dashboard cleanliness.
* **Fulfillment Rate:** Tracks customer service level execution by evaluating actual volume supplied against true market prescription demand. It incorporates internal boundaries ensuring supply ceilings do not artificially inflate fulfillment beyond 100%.
* **Output Variance:** Establishes the absolute physical delta between manufacturing schedule expectations and actual factory floor realities. A negative figure immediately signals production friction or line inefficiencies.
* **Material Wastage %:** Quantifies manufacturing yield optimization by isolating the volume of scrapped or wasted physical product relative to the total actual output volume produced.
* **Stock-out Risk:** Dynamically evaluates distribution vulnerabilities by comparing the remaining supply buffers against critical safety inventory thresholds (set at 15% of demand), generating binary warning flags for high-risk assets.
* **Average Transit Delays:** Tracks logistical execution and dispatch bottlenecks by calculating the true calendar day variance between actual arrival timestamps and original expected shipment arrival baselines.

![DAX Implementation](https://github.com/SOMTO-2006/Pharma-supply-chain-analytics/blob/main/Pharma%20Dashboard%20Dax%20View.png)

---

## 🚀 Key Business Insights Driven by this Solution
1. **The Production Disconnect:** Despite hitting a **100% Fulfillment Rate**, the factory suffered a negative **Output Variance of -2,275 units**. This reveals that while current client demands were met, production inefficiencies or scheduling friction exist that could threaten future baseline buffers.
2. **Operational Bottlenecks:** The 78% factory efficiency score coupled with localized trend lines isolates specific periods in mid-May where yield dipped significantly, giving plant managers the precise temporal target needed for process retrospectives.
3. **Cross-Regional Traceability:** Stakeholders can now dynamically slice by specific European territories or individual drug assets to evaluate regional supply chain exposure in under 2 seconds.

---

