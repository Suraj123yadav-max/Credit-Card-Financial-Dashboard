<div align="center">

# 💳 Credit Card Financial Dashboard

### End-to-end analytics project — SQL data pipeline + Power BI dashboard for credit card operations

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](#)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![SQL](https://img.shields.io/badge/SQL-025E8C?style=for-the-badge&logo=amazonaws&logoColor=white)](#)
[![DAX](https://img.shields.io/badge/DAX-E6522C?style=for-the-badge&logo=powerbi&logoColor=white)](#)

**Turns 10,000+ rows of raw credit card & customer data into a live, filterable executive dashboard.**

</div>

---

## 🎯 Project Objective

To design and build a comprehensive credit card dashboard that delivers **real-time insight into revenue, interest income, customer behavior, and transaction trends** — giving stakeholders a single source of truth to monitor and analyze credit card operations weekly, instead of digging through raw exports.

This project simulates a real-world BI workflow end-to-end: **raw CSVs → SQL database → data model → DAX measures → interactive Power BI report.**

---

## 🖼️ Dashboard Preview

<table>
<tr>
<td align="center" width="50%">
<b>Customer Report</b><br/>
<img src="assets/customer_report.jpg" alt="Credit Card Customer Report" width="100%"/>
</td>
<td align="center" width="50%">
<b>Transaction Report</b><br/>
<img src="assets/transaction_report.jpg" alt="Credit Card Transaction Report" width="100%"/>
</td>
</tr>
</table>

> Full-resolution exports are also available as PDFs in this repo: [`Customer Report`](<Credit Card Financial Dashboard-Customer.pdf>) · [`Transaction Report`](<Credit Card Financial Dashboard-Transaction.pdf>) · [`Weekly Status Report`](<Credit Card Financial Weekly Dashboard Report.pdf>)

---

## 📈 Key Insights Surfaced by the Dashboard

- 💰 **$55.4M** total revenue and **$7.9M** total interest earned analyzed across a full year of weekly data
- 🥇 The **Blue** card tier alone drives roughly **80%+ of total revenue**, far ahead of Silver, Gold, and Platinum combined
- 📲 **Swipe transactions (35M)** are more than double Chip (17M) and over 10x Online (3M) — a clear channel-risk signal for fraud/security prioritization
- 👥 Revenue is concentrated in customers aged **30–50**, graduate-educated, and married — a clear target segment for retention campaigns
- 🗺️ **Texas, New York, and California** are the top 3 revenue-generating states
- ⭐ Tracked a **Customer Satisfaction Score (CSS)** and **Customer Acquisition Cost** side-by-side with revenue to connect experience metrics to financial outcomes

---

## 🧠 Skills Demonstrated

| Area | What I did |
|---|---|
| **Data Engineering** | Designed a relational schema, wrote SQL `CREATE TABLE` / `COPY` scripts to load 4 raw CSVs into PostgreSQL, and handled real-world data issues (date formatting errors, incremental "Week-53" backfills) |
| **Data Modeling** | Built a star-schema-style relationship between transaction (`cc_detail`) and customer (`cust_detail`) tables on `Client_Num` inside Power BI |
| **DAX & Analysis** | Authored measures for revenue, interest earned, utilization ratio, and quarter-over-quarter trends |
| **Dashboard Design** | Built two purpose-driven report pages (Customer vs. Transaction) with a shared, synced filter panel (quarter, week, income band, card tier, gender) for fast cross-filtering |
| **Storytelling** | Packaged findings into a weekly status report (PDF) summarizing objective, method, and takeaways for a non-technical audience |

---

## 🗂️ Repository Structure

```
Credit_Card_Financial_Dashboard/
├── assets/
│   ├── customer_report.jpg
│   └── transaction_report.jpg
├── credit_card.csv                                  # Weekly transaction data (2023)
├── customer.csv                                      # Customer demographic data
├── cc_add.csv                                         # Week-53 supplementary transaction data
├── cust_add.csv                                       # Week-53 supplementary customer data
├── SQL Query - Financial Dashboard Data.sql           # DB setup + CSV ingestion script
├── Credit Card Financial Dashboard-Customer.pdf       # Customer report export
├── Credit Card Financial Dashboard-Transaction.pdf    # Transaction report export
├── Credit Card Financial Weekly Dashboard Report.pdf  # Weekly status summary
└── README.md
```

> 💡 Add your `.pbix` file to the repo root if you want recruiters/visitors to open the live, interactive report in Power BI Desktop.

---

## 🏗️ Data Model & Pipeline

```
CSV Sources                SQL (PostgreSQL)              Power BI
──────────────            ──────────────────            ─────────────
credit_card.csv    ──▶    cc_detail table       ──▶     Data Model
customer.csv        ──▶   cust_detail table      ──▶    (joined on
cc_add.csv (wk-53)  ──▶   appended to cc_detail          Client_Num)
cust_add.csv (wk-53)──▶   appended to cust_detail  ──▶   DAX Measures
                                                    ──▶   Report Pages
```

**`cc_detail`** — one row per customer per week
- Card details: `Card_Category`, `Annual_Fees`, `Credit_Limit`, `Customer_Acq_Cost`
- Activity: `Total_Revolving_Bal`, `Total_Trans_Amt`, `Total_Trans_Ct`, `Avg_Utilization_Ratio`
- Channel & spend: `Use_Chip`, `Exp_Type`, `Interest_Earned`, `Delinquent_Acc`
- Time: `Week_Start_Date`, `Week_Num`, `Qtr`, `current_year`

**`cust_detail`** — one row per customer
- Demographics: `Customer_Age`, `Gender`, `Dependent_Count`, `Education_Level`, `Marital_Status`
- Location: `State_cd`, `Zipcode`
- Assets & job: `Car_Owner`, `House_Owner`, `Personal_Loan`, `Customer_Job`, `Income`
- Engagement: `Cust_Satisfaction_Score`

---

## 📊 Dashboard Pages

### 1️⃣ Customer Report — *who are the customers driving revenue?*
- **KPIs:** Total Revenue · Total Interest · Total Income · Customer Satisfaction Score
- Revenue trend by gender over time
- Revenue by age group, salary band, dependent count, marital status, education level
- Top 5 states by revenue
- Revenue by customer occupation
- Filters: quarter, week, income band (Low/Mid/High), card tier (Platinum/Gold/Silver/Blue)

### 2️⃣ Transaction Report — *how are the cards being used?*
- **KPIs:** Total Revenue · Total Interest · Transaction Amount · Transaction Count
- Revenue and transaction count trend by quarter
- Revenue by card category, expenditure type, education level, customer job
- Revenue by transaction channel (Swipe / Chip / Online)
- Customer acquisition cost by card tier

Both pages share the same filter panel, so anyone clicking through the live file can pivot instantly between the "who" and "how" views without losing context — a deliberate UX choice to make the report feel like one connected tool rather than two disconnected charts.





---

## 🛠️ Tech Stack

`PostgreSQL` · `SQL` · `Power BI` · `DAX` · `Power Query` · `Excel / CSV`

---


