# Adidas US Sales Analysis — Business & Data Analysis

> **From Data to Decisions**
> A Power BI (with an Excel companion) analytics project built to move beyond static reporting toward **diagnostic ("why") analysis** and **forward-looking (what-if / forecast) decision support** for Adidas' US sales performance — closed out with a boardroom-ready executive presentation summarizing the story for stakeholders.

![Home Page](<Power BI/Screenshot 2026-03-25 140015.png>)

---

## Project Overview

**Adidas US Sales Analysis** is a Power BI report (backed by an Excel workbook) built to give a multi-dimensional view of sales and profitability across retailers, regions, states, cities, products, and sales channels.

The report is designed so that a single landing page can answer the majority of common business questions on its own, with every visual cross-filtered — clicking any data point (a month, a state, a product) instantly updates every other visual on the page. Anything that needs deeper explanation is one click away through dedicated drill-through and diagnostic pages.

**Analytical flow:**

```
Raw Data → Data Preparation → Data Modeling → KPI Layer → Diagnostic Analysis (Why) → Scenario Analysis (What-If) → Forecast → Executive Reporting → Decision Support
```

The journey is deliberately end-to-end: the same numbers that live inside an interactive Power BI model are also distilled into a polished executive presentation ([`Adidas_Analysis.pptx`](Adidas_Analysis.pptx)) — because a good analyst doesn't just build a dashboard, they also know how to tell its story to people who will never open Power BI.

## Business Objectives

The report is designed to answer questions such as:

- How are total sales and operating profit trending, and how do they compare to target?
- Which regions, states, cities, retailers, and products are driving performance?
- **Why** did sales or profit rise or fall for a specific product in a specific month?
- Which sales channel — In-store, Online, or Outlet — performs best in which market?
- What would happen to sales and profit under a different price, quantity, or cost scenario?
- What level of sales should we expect in the coming months, and for which products, so production can meet demand without over-accumulating inventory?

## Repository Structure

```
Adidas-Analysis/
│
├── README.md
├── Adidas_Analysis.pptx         # Executive summary presentation (10 slides)
│
├── Excel/
│   ├── ADIDAS sales.xlsx        # Dataset, pivot tables, and Excel dashboard
│   └── Screenshot ....png       # Excel dashboard screenshot
│
└── Power BI/
    ├── Dashboard.pbix           # Full Power BI report
    └── Screenshot ....png (×9)  # Report page screenshots
```

## Data

The dataset (`Dataset` sheet in `ADIDAS sales.xlsx`) covers **9,648 transaction records** across **2020–2021** in the US market, with the following fields:

`Retailer` · `Retailer ID` · `Invoice Date` · `Region` · `State` · `City` · `Sales Method` · `Product` · `Price per Unit` · `Units Sold` · `Total Sales` · `Operating Profit` · `Operating Margin`

The workbook also includes supporting sheets — `Sales Pivots`, `Sales Dashboard`, `Financial Pivot`, and `Financial Dashboard` — used to prepare and cross-check the figures behind the Power BI model.

## Dashboard Structure

### 1. Home / Sales Performance

The landing page combines a KPI layer with fully cross-filtered visuals — Year, Month, Product, and State slicers instantly update every card and chart on the page:

- **Total Sales** and **Operating Profit** KPI cards
- **Actual vs. Target** gauge — the target is deliberately set at **10% growth over the previous month's sales** rather than an arbitrary "beat last month" benchmark, to track a sustainable growth rate instead of chasing short-term spikes
- **Profit Product Details** table — click any product row to see its individual performance
- A **Sales / Profit toggle button** to switch the whole page's context between the two views
- Sales and profit trend over months, and profit/sales by state

**Purpose:** a single page that answers most of the report's core business questions in one click, without needing to navigate further.

![Sales Performance](<Power BI/Screenshot 2026-03-25 140139.png>)

### 2. Diagnostic Drill-Through — "Why Sales" / "Why Profit"

Right-clicking any point on the monthly trend chart and selecting **Drill through → Why Sales / Why Profit** breaks the number down along **Region → State → City → Retailer → Sales Method → Product**, so a specific movement (e.g., a drop in Men's Apparel sales in a given month and state) can be traced to its source in a few clicks.

Conditional formatting on this page communicates the story at a glance:

- 🔴 **Red** — performance decreased vs. the previous month
- 🟢 **Green** — performance increased vs. the previous month (with the growth % shown)
- 🔵 **Blue** — no prior-month sales exist for that segment to compare against

![Why Sales](<Power BI/Screenshot 2026-03-25 140436.png>)

### 3. Sales Channels

A decomposition tree lets the analysis be built up interactively — **Region → State → City → Retailer → Sales Method → Product** — to understand which sales channel (In-store, Online, or Outlet) performs best in a given market.

**Purpose:** support channel-mix decisions and customer targeting — for example, identifying states or cities where the **Outlet** channel consistently outperforms can indicate a more price-sensitive customer base, guiding which products and markets to prioritize.

![Sales Channels](<Power BI/Screenshot 2026-03-25 140455.png>)

### 4. What-If Analysis

A scenario page with three parameters — **Price %**, **Quantity %**, and **Cost %** — plus a **Product slicer**, so the impact of a specific change (for example, a 5% price increase on Men's Apparel) can be simulated at the product level.

A fixed baseline card (Total Sales / Operating Profit, unaffected by the parameters) is kept alongside the simulated "Sales If / Profit If" cards, so the scenario can always be compared directly against the actual baseline.

![What If Analysis](<Power BI/Screenshot 2026-03-25 141153.png>)

### 5. Forecasting

Monthly sales and profit forecast with a **95% confidence interval** (upper/lower bound), filterable by product, to help decision-makers plan production against expected demand without over-accumulating inventory.

**Limitation, by design:** the forecast is a statistical projection based only on the historical data in the model — it does not account for external economic or marketing factors, which can materially affect actual future results.

![Forecasting](<Power BI/Screenshot 2026-03-25 141215.png>)

## Key Business Insight

Filtering the report to the first year shows relatively weak sales (~$183M), while the following year jumps to ~$717.8M — a **294% YoY growth rate**, visible directly on the Home page's growth badge. Breaking this down on the column chart after filtering to the later year shows why: Adidas sold in only **9 US states in 2020**, expanding to **all 50 states in 2021** — full national coverage, not just organic growth, was the real driver behind the jump.

## Executive Report — From Dashboard to Boardroom

Not every stakeholder wants to open a `.pbix` file and click through slicers — some just want the story and the numbers. That's the gap **[`Adidas_Analysis.pptx`](Adidas_Analysis.pptx)** closes: a 10-slide executive presentation that takes the same underlying model and turns it into a narrative a business audience can read in five minutes.

**The story it tells, slide by slide:**

1. **Cover** — *Adidas Sales & Profit Analysis, FY 2020–2021* — framing the scope up front: revenue, profitability, product mix, and channel performance.
2. **Goals of the discussion** — three questions the whole deck is built to answer: where are the peak/decline months (and where is this headed), how is each product performing, and how are sales and profit split across channels.
3. **Headline KPIs** — Total Sales **$899.9M**, Operating Profit **$332.13M** (▲324.07%), Units Sold **2,478,861** (▲294.23%) — with the "so what": profit growing *faster* than sales points to improving cost control and margins, not just higher volume.
4. **Geographic expansion** — the **9 → 50 states** story, with a state-level sales & profit bar chart making the national rollout visible at a glance.
5. **Monthly trend** — sales and profit plotted together across the year, so peak months (July, August) and softer months (March, October) are immediately visible.
6. **Product performance breakdown** — a full sales/profit/units table by product; **Men's Street Footwear leads on both sales ($208.8M) and profit ($82.8M)**, making it the clear top performer across the whole period.
7. **Channel distribution** — In-store leads at **~39–40%**, with Outlet (~33%) and Online (~27–29%) close behind on both sales and profit — a near-identical split that signals channel economics are consistent, not skewed by discounting in any one channel.
8. **2022 forecast outlook** — sales and profit projected forward into early 2022, pointing to continued upward momentum.
9. **Key takeaways** — four one-line executive callouts: Revenue Growth, Profit Surge, Channel Mix, and 2022 Forecast — the "if you only remember four things" slide.
10. **Close** — data scope and attribution, tying the deck back to the underlying FY 2020–2021 dataset.

**Purpose:** this is the deliverable that turns the analysis into a decision-ready story — the same discipline used to build the Power BI model (clear KPIs, a clean narrative arc, one insight per visual) applied to a format a CFO or brand manager can act on without touching the report itself.

## Filters & Interactivity

A consistent slicer set — **Year, Month, Product, State/Region/City, Retailer, Sales Method** — is available across the relevant pages, and every visual on a page is cross-linked so a single click (on a bar, a point, or a table row) filters the entire page instead of just one chart.

## Technology Stack

| Technology | Role |
|---|---|
| **Power BI** | Data modeling, DAX measures, drill-through pages, decomposition tree, What-If parameters, forecasting |
| **DAX** | KPIs, dynamic targets, conditional formatting logic |
| **Microsoft Excel** | Data preparation, pivot tables, and a standalone Excel sales dashboard |
| **Microsoft PowerPoint** | Executive summary presentation for non-technical stakeholders |

## Key Analytical Concepts

Business Intelligence · Data Modeling · DAX · Drill-Through Analysis · Root-Cause ("Why") Analysis · Conditional Formatting · Decomposition Tree · Sales Channel Analysis · What-If Scenario Analysis · Time-Series Forecasting · Confidence Intervals · Dynamic Target Setting · YoY Growth Analysis · Customer/Channel Segmentation · Executive Reporting · Data Storytelling

## Navigation

```
Home / Sales Performance
 ├── Why Sales (drill-through)
 ├── Why Profit (drill-through)
 ├── Sales Channels
 ├── What-If Analysis
 └── Forecasting
```

## Limitations

- The dataset covers the **US market only**, across **2020–2021** — conclusions should be read within that scope.
- No customer-level or demographic data is available; channel-level signals (In-store/Online/Outlet) are used as a proxy for market behavior instead.
- The forecast page reflects historical patterns only and does not incorporate external economic or marketing variables.

## Project Value

This project is not just "a Power BI dashboard" — it is built around a specific question at every page: **why did this happen, and what should we do next?** From a single cross-filtered landing page, to root-cause drill-throughs, to scenario simulation and forecasting, the report is structured to move a user from *what happened* to *why it happened* to *what to do about it*.

It also demonstrates a skill many dashboards skip: **knowing when to stop clicking and start writing.** The same model that powers the interactive Power BI report is distilled into a concise executive presentation — proof that the analysis doesn't just live inside a tool, it can be communicated, defended, and acted on in a boardroom.

## Author

**Hady Amr**
**Business & Data Analyst**

- 🔗 LinkedIn: [linkedin.com/in/hadyamr](https://linkedin.com/in/hadyamr)
- 💻 GitHub: [github.com/hadyam](https://github.com/hadyam)

## Disclaimer

This repository is a portfolio/analytical project. The dashboard and analysis are intended to demonstrate data analytics, business intelligence, modeling, and decision-support skills. Conclusions should be interpreted within the scope, quality, and time period of the underlying dataset.
