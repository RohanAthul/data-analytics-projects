# ⚡ Electric Vehicle Market Dashboard — Power BI

A multi-page Power BI dashboard exploring the global EV market across performance, pricing, and value metrics. Built as a portfolio project using a real-world dataset of electric vehicles with specs, range, efficiency, and multi-market pricing.

---

## 📊 Dashboard Pages

| Page                    | Status     | Description |
|-------------------------|------------|-------------|
| Market Overview         | ✅ Done    | KPI cards, drive config donut, brand treemap, market valuation stacked bar |
| Performance Explorer    | 🚧 WIP     | Battery vs range scatter, speed comparisons, fastcharge rankings |
| Price vs Value Analysis | 📝 TBD     | Multi-market pricing, DAX value score, best-value model matrix |

---

## 🗂️ Dataset

The dataset contains detailed specifications and pricing information for a wide range of electric vehicle models.

### Columns:

| Column                                | Description |
|---------------------------------------|-----------|
| `Row_ID`                              | Unique identifier for each record |
| `Brand` / `Model`                     | Vehicle brand and model name |
| `Drive_Configuration`                 | RWD / FWD / AWD |
| `Battery`                             | Battery capacity (kWh) |
| `RangeValue`                          | Price per km of range (€) — combines affordability and range; lower is better |
| `Range`                               | Estimated real-world range (km) |
| `Efficiency`                          | Energy consumption (Wh/km) |
| `0-100`                               | Acceleration 0–100 km/h (seconds) |
| `Top_speed`                           | Top speed (km/h) |
| `Fastcharge`                          | Fast charging speed (km/h added) |
| `Number_of_seats`                     | Seating capacity |
| `Towbar_possible`                     | Whether a towbar can be fitted (Yes/No) |
| `Towing_capacity_in_kg`               | Maximum towing capacity (kg) |
| `Germany_price_before_incentives`     | List price in Germany before incentives (€) |
| `Netherlands_price_before_incentives` | List price in Netherlands before incentives (€) |
| `UK_price_after_incentives_EUR`       | Price in UK after government incentives (converted to EUR) |
| `Approx_price_in_USD`                 | Approximate price in the US market (USD) |

> **Note:** All prices except the UK column are before incentives. The UK price is post-incentive and converted to EUR. US price is an approximation.

---

## 🔍 Page 1 — Market Overview

**Status: 🚧 Work in Progress**

A high-level snapshot of the EV market intended for quick executive-style reading.

**Visuals included:**
- KPI cards — avg range (km), avg efficiency (Wh/km), avg 0–100 km/h, total brands
- Donut chart — drive configuration distribution (AWD / RWD / FWD) with count and percentage labels
- Treemap — brand representation volume, sized by number of models
- 100% stacked bar chart — market valuation split across Germany, Netherlands, UK, and US for top manufacturers

![Page 1 – Market Overview](images/page1_market_overview.jpeg)

---

## 🏎️ Page 2 — Performance Explorer

**Status: 🚧 Work in Progress**
---

## 💰 Page 3 — Price vs Value Analysis

**Status: 📝 TBD**

Multi-market pricing comparison with a custom DAX value score to identify the best value EVs.
