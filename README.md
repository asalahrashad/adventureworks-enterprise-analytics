# 🚴‍♂️ AdventureWorks Enterprise Analytics
> **Enterprise Business Intelligence Solution built with Power BI, DAX, & SQL Server.**

An enterprise-grade BI solution that delivers actionable insights for senior executive management. This project strictly follows modern data architecture by separating the **Centralized Semantic Model** from the **Reporting Layer** to ensure a single source of truth, high scalability, and optimized performance.

---

## 🗺️ Solution Architecture & Data Modeling
The project is built on top of the Microsoft **AdventureWorksDW**. It implements a robust **Star Schema** centered around **Conformed Dimensions** to eliminate fact-to-fact ambiguity and deliver sub-second query performance.

### 📊 Enterprise Bus Matrix
| Dimension Table | FactInternetSales (B2C) | FactResellerSales (B2B) | FactSalesQuota (Targets) | FactCurrencyRate (Rates) |
| :--- | :---: | :---: | :---: | :---: |
| **DimDate** | ✅ Conformed | ✅ Conformed | ✅ Conformed | ✅ Conformed |
| **DimProduct** | ✅ Conformed | ✅ Conformed | ❌ N/A | ❌ N/A |
| **DimSalesTerritory** | ✅ Conformed | ✅ Conformed | ❌ Indirect | ❌ N/A |
| **DimEmployee** | ❌ N/A | ✅ Direct | ✅ Direct | ❌ N/A |
| **DimCustomer** | ✅ Direct | ❌ N/A | ❌ N/A | ❌ N/A |
| **DimReseller** | ❌ N/A | ✅ Direct | ❌ N/A | ❌ N/A |
| **DimPromotion** | ✅ Direct | ✅ Direct | ❌ N/A | ❌ N/A |
| **DimCurrency** | ✅ Conformed | ✅ Conformed | ❌ N/A | ✅ Conformed |

---

## 📱 App 1: Executive Overview Dashboard
A high-end, light-minimalist analytical application structured to answer critical business questions in under 5 minutes using a strict top-down layout design.

### 🏢 1. Executive Summary (The Horizon)
* **Goal:** 30-second health check for C-Suite executives.
* **KPIs:** Total Revenue, Gross Profit, Gross Margin %, Total Orders (All with YoY Growth contexts).
* **Visuals:** Revenue & Profit Monthly Trend, Revenue Split (Internet vs Reseller), Regional Profitability Map, Product Category Growth Matrix.

### 📈 2. Sales Performance (Deep Dive)
* **Goal:** Granular breakdown of sales channels, volumes, and customer behavior.
* **KPIs:** Internet Sales, Reseller Sales, Average Order Value (AOV), Total Quantity.
* **Visuals:** Revenue Split Donut (with smart tooltips), Top 10 Products by Channel, Regional Revenue Treemap.

### 💸 3. Profitability Analysis (Financial Leakage)
* **Goal:** Trace where money is spent and detect margin drops.
* **KPIs:** Gross Profit, Gross Margin %, Total Cost, Freight & Tax Summary.
* **Visuals:** Revenue-to-Profit Waterfall Bridge, Margin vs Cost Line Combo, Product Subcategory Profitability Matrix (Scatter).

### 🎯 4. Business Performance & Quotas (Operations)
* **Goal:** Evaluate sales team efficiency against targets and track B2B performance.
* **KPIs:** Quota Achievement %, Target Variance, Active Employees, Active Resellers.
* **Visuals:** Actual Sales vs Quota Trend, Employee Target Achievement Ranking (Conditional Formatting), Promotion Contribution Funnel.

### 💡 5. Executive Insights (Actionable Data)
* **Goal:** Instant highlighting of the business extremes (The Peaks and Troughs).
* **KPIs:** Best Employee, Top Territory, Best Selling Product, Underperforming Market.
* **Visuals:** Top 10 vs Bottom 10 Products, VIP Reseller Accounts, Lowest Performing Territories.

---

## ⚡ Technical Highlights & Advanced DAX
* **Centralized Semantic Model:** Built using Thin Reports connected to a single published dataset via Live Connection.
* **Dynamic Currency Conversion:** Implemented dynamic translation utilizing `FactCurrencyRate` to handle local reseller pricing vs standard USD costs.
* **Time Intelligence Framework:** Custom DAX logic for `YoY Growth %`, `YTD`, and `Prior Year` calculations without breaking cross-filtering.
* **Strict Measure Organization:** Folder and Sub-folder structures managed via Tabular Editor for maximum scannability.

---

## 🛠️ Technology Stack
* **SQL Server / T-SQL:** Data Warehouse hosting, schema exploration, and data validation.
* **Power BI Desktop:** Semantic modeling, DAX engineering, and UX/UI dashboard development.
* **Tabular Editor:** Advanced model scripting and measure organization.
* **DAX Studio:** Query optimization and performance tuning of the VertiPaq engine.

---

## 📂 Repository Structure
```text
AdventureWorks-Enterprise-Analytics
│
├── sql/               # T-SQL Scripts for DW analysis & validation
├── dax/               # Centralized DAX Measures catalog (.txt/.dax)
├── powerbi/           # Power BI Templates (.pbit) and Reports (.pbix)
├── docs/              # Architecture details, Wireframes, and Bus Matrix
└── README.md          # Project Documentation
