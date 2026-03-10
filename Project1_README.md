# 🏦 Canadian Big 5 Banks — Stock Performance Dashboard

![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=sqlite&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

## 📊 Live Dashboard
🔗 [View on Tableau Public](https://public.tableau.com/app/profile/ven.anusuri/viz/CanadianBig5Banks-StockPerformanceDashboard/Dashboard1?publish=yes)

---

## 📌 Project Overview

This project analyzes the stock performance of Canada's Big 5 banks — **TD Bank, Royal Bank (RY), BMO, Scotiabank (BNS), and CIBC** — over a 5-year period from March 2021 to March 2026.

As a financial advisor with 3+ years of experience at TD Bank, I built this dashboard to combine my deep domain knowledge of the Canadian banking sector with data analytics skills. The goal was to tell a meaningful story about how Canadian banks performed through some of the most significant economic events in recent history.

---

## 🎯 Business Questions Answered

- Which Canadian bank delivered the strongest stock price growth from 2021 to 2026?
- How did the **2022 Bank of Canada rate hike cycle** impact bank stock prices?
- What does the **30-day moving average** reveal about each bank's price momentum?
- How does each bank's average yearly stock price compare year over year?

---

## 📈 Dashboard Features

| Chart | Description |
|-------|-------------|
| **Stock Price Trend** | Multi-line chart showing daily closing prices for all 5 banks (2021–2026) |
| **Average Yearly Stock Price** | Horizontal grouped bar chart comparing each bank's average price by year |
| **Moving Average vs Actual Price** | Dual-axis line chart showing 30-day moving average vs actual closing price |

---

## 🛠️ Tools & Technologies

- **SQL (SQLite / DB Browser)** — Data cleaning, filtering, and reshaping from wide to long format
- **Python (Pandas)** — Data transformation and date filtering
- **Tableau Public** — Dashboard design and visualization
- **Kaggle** — Source dataset (Top 50 Canadian Stocks Since 2010)

---

## 📂 Data Source

- **Dataset:** [Top 50 Canadian Stocks Since 2010](https://www.kaggle.com/) — Kaggle (Harbhajan Singh)
- **Tickers Used:** TD.TO, RY.TO, BMO.TO, BNS.TO, CM.TO (Toronto Stock Exchange)
- **Date Range:** March 1, 2021 — March 1, 2026
- **Currency:** CAD (Canadian Dollars)

---

## 🧹 Data Cleaning Process

The raw dataset required significant cleaning before visualization:

1. **Format conversion** — Reshaped from wide format (each bank as a column) to long format (one row per bank per date) using SQL and Python
2. **Date filtering** — Filtered to 2021–2026 to focus on the post-COVID economic cycle
3. **Null removal** — Removed rows with missing closing prices
4. **Column renaming** — Standardized ticker symbols to full bank names for readability

**SQL Query used for cleaning:**
```sql
SELECT 
    Date,
    "TD.TO"  AS TD_Bank,
    "RY.TO"  AS Royal_Bank,
    "BNS.TO" AS Scotiabank,
    "BMO.TO" AS BMO,
    "CM.TO"  AS CIBC
FROM top_50_canadian_stocks_data_since_2010
WHERE Date >= '2021-03-01' 
  AND Date <= '2026-03-01'
  AND "TD.TO"  IS NOT NULL
  AND "RY.TO"  IS NOT NULL
  AND "BNS.TO" IS NOT NULL
  AND "BMO.TO" IS NOT NULL
  AND "CM.TO"  IS NOT NULL
ORDER BY Date ASC;
```

---

## 💡 Key Insights

- **Royal Bank (RY)** consistently maintained the highest stock price, reflecting its position as Canada's largest bank by market cap
- **All 5 banks showed a notable dip in mid-2022**, coinciding with the Bank of Canada's aggressive rate hike cycle
- **Strong recovery from 2023 onwards** across all banks, with Royal Bank and BMO showing the steepest growth
- **Scotiabank and TD** showed more modest growth, consistent with their higher international exposure
- The **30-day moving average** confirms sustained upward momentum despite short-term volatility

---

## 🗂️ Repository Structure

```
📁 canadian-banks-stock-dashboard/
├── 📄 README.md
├── 📁 data/
│   └── canadian_banks_tableau_ready.csv
├── 📁 sql/
│   └── data_cleaning.sql
├── 📁 screenshots/
│   └── dashboard_overview.png
```

---

## 🔮 Future Enhancements

- Add **Bank of Canada interest rate overlay** to show rate vs stock price correlation
- Include **dividend yield analysis** for income-focused investors
- Expand to include **US bank comparison** (JPM, BAC)
- Add **trading volume analysis**

---

## 👤 About Me

**Ven Anusuri** | Financial Advisor → Data Analyst

- 3+ years experience as a Financial Advisor at **TD Bank**
- Certifications: CSC, PFSA, FP-1, BCO, Google Data Analytics, Bloomberg Market Concepts
- Building a 10-project data analytics portfolio bridging finance domain expertise with data skills

🔗 [Tableau Public Profile](https://public.tableau.com/app/profile/ven.anusuri)

---
*Project 1 of 10 — Financial Data Analytics Portfolio*
