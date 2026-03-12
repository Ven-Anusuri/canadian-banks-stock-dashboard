# Canadian Big 5 Banks — Stock Performance Dashboard

**Live Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/ven.anusuri/viz/CanadianBig5Banks-StockPerformanceDashboard/Dashboard1?publish=yes)

---

## Why I Built This

After three years as a financial advisor at TD Bank, I've had countless conversations with clients about the Big 5 — how they compare, which ones held up during rate hikes, why Royal Bank always seems to command a premium. I wanted to stop answering those questions from memory and start answering them with data.

This dashboard is the result of that. I pulled five years of daily stock data for TD, RBC, BMO, Scotiabank, and CIBC, cleaned it up with SQL and Python, and built an interactive Tableau dashboard that tells the full story of how these banks have performed from 2021 through early 2026 — through rate hike cycles, economic uncertainty, and recovery.

---

## What the Dashboard Shows

**Stock Price Trends (2021–2026)**
A multi-line chart tracking daily closing prices for all five banks side by side. You can see exactly when they moved together and when they diverged.

**Average Yearly Stock Price**
A grouped bar chart that makes it easy to compare each bank's average price year over year — useful for spotting which banks compounded gains steadily versus which ones had more volatile years.

**30-Day Moving Average vs. Actual Price**
A dual-axis view that strips out the day-to-day noise and highlights the underlying momentum for each bank.

---

## The Questions I Wanted to Answer

- Which bank delivered the strongest growth over the five-year window?
- How did the 2022 Bank of Canada rate hike cycle actually show up in stock prices?
- Does the 30-day moving average confirm the recovery story, or is it messier than it looks?
- How do the banks stack up year by year on average price?

---

## Data & Tools

| | |
|---|---|
| **Dataset** | Top 50 Canadian Stocks Since 2010 — [Kaggle](https://www.kaggle.com/) (Harbhajan Singh) |
| **Tickers** | TD.TO, RY.TO, BMO.TO, BNS.TO, CM.TO |
| **Date Range** | March 1, 2021 — March 1, 2026 |
| **Currency** | CAD |
| **Cleaning** | SQL (SQLite / DB Browser) + Python (Pandas) |
| **Visualization** | Tableau Public |

---

## How I Cleaned the Data

The raw dataset came in wide format — one column per bank, one row per date. That's not what Tableau wants. I used SQL to reshape it into long format, filter the date range, and drop any rows with missing closing prices. Then I did some final column renaming in Python to swap the ticker symbols for readable bank names.

Here's the core SQL I used:

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

## What I Found

A few things stood out that matched my intuition from working in the industry — and a couple that surprised me.

Royal Bank held the highest stock price throughout the entire period, which makes sense given its position as Canada's largest bank by market cap. What was interesting was how consistently it maintained that gap even during the rough patches.

The mid-2022 dip is clearly visible across all five banks, right in line with when the Bank of Canada started its aggressive rate hike cycle. Clients were worried during that period — this chart shows why.

From 2023 onward, the recovery is real. Royal Bank and BMO led it. TD and Scotiabank lagged — consistent with their heavier international exposure creating more uncertainty for investors.

The 30-day moving average tells a cleaner version of the same story: sustained upward momentum from 2023 to 2026, with short-term volatility smoothed out.

---

## What's Next

A few things I want to add when time allows:

- Dividend yield data — for a lot of my former clients, income was the whole point of holding bank stocks
- A US bank comparison (JPM, BAC) to put Canadian performance in a North American context
- Trading volume overlays to flag periods of unusual market activity
- User-controlled filters so you can isolate individual banks or date ranges

---

## Repository Structure

```
canadian-banks-stock-dashboard/
├── README.md
├── Project1_README.md
└── canadian_banks_tableau_ready.csv
```

---

## About Me

I'm Ven Anusuri — currently transitioning from financial advisory into data analytics. I spent three years at TD Bank helping clients make sense of their finances, and I'm now building a 10-project portfolio that combines that industry knowledge with hands-on analytics skills.

Certifications: CSC, PFSA, FP-1, BCO, Google Data Analytics, Bloomberg Market Concepts, and a few more in progress.

[Tableau Public Profile](https://public.tableau.com/app/profile/ven.anusuri)
