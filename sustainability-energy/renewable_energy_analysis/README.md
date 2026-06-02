# 🌱 Renewable Energy World Wide: 1965–2022

A data analysis project exploring global renewable energy trends across six decades, from the post-Industrial era through the modern green transition.

## 📋 Overview

Since the Industrial Revolution, the energy mix of most countries has been dominated by fossil fuels — with major implications for global climate and human health. This project investigates how rapidly renewable energy production is changing worldwide, and which technologies and nations are leading the transition.

Using a comprehensive dataset spanning **1965 to 2022**, this analysis covers hydropower, wind, solar, biofuel, and geothermal energy production across countries and regions globally.

**Key questions explored:**
- How has the global renewable energy share evolved over time?
- Which countries are leading — and which are falling behind?
- What impact have major climate agreements (Kyoto, Paris) had on real-world energy data?
- When, at current trajectories, might countries reach 100% renewable energy?

---

## 📁 Project Structure

```
├── data/
│   └── 01 renewable-share-energy.csv   # Source dataset
├── renewable_energy_analysis.ipynb     # Main Jupyter notebook
└── README.md
```

---

## 📊 Dataset

| Column | Description |
|--------|-------------|
| `Entity` | Country or region name |
| `Code` | ISO 3-letter country code |
| `Year` | Year of record |
| `Renewables (% equivalent primary energy)` | Share of primary energy from renewable sources |

The dataset is split into three subsets for analysis:
- **World** — global aggregate
- **Countries** — individual country data
- **Aggregates** — income groups, continents, and BP regions

---

## 🔍 Analysis Highlights

### Time Series Trend Analysis
A 10-year rolling average reveals three distinct historical phases:

- **The Plateau (1970–2000):** Renewable share stagnated between 6–8%, dominated by traditional hydropower.
- **The Inflection Point (~2005–2010):** Costs of solar and wind began dropping; global climate policies took effect.
- **Hockey Stick Growth (2015–2021):** Share surpassed 13%, more than doubling from the 1965 baseline.

> **The green transition took 40 years to grow by 2%, but leaped by 5% in the last decade alone.**

### Policy Impact: Kyoto vs. Paris
- **Kyoto Protocol (1997):** Shows a ~10-year lag before renewable infrastructure effects appear in data.
- **Paris Agreement (2015):** Coincided with, and accelerated, an already-building trend. Post-2015 yearly growth is **6× faster** than pre-2015.
- **2020 Anomaly:** A COVID-driven spike — total energy demand dropped while low-marginal-cost renewables kept running, inflating the percentage share.

### Top Performers (2021)
Iceland leads with **86.9%** of its energy from renewables, driven by unique geothermal and hydroelectric geography. Four of the top ten countries are Nordic. Brazil (46.2%) and Colombia (33.0%) represent strong South American hydropower capacity.

### Fastest Climbers (1990–2021)
Denmark added nearly **38 percentage points** — the largest absolute gain globally — through aggressive offshore wind expansion. Germany and the UK also built their renewable capacity almost entirely from scratch since 1990.

### Linear Trajectory Forecasting
A `LinearRegression` model (trained on post-2005 data) projects when countries might reach 100% renewables at current velocity:

| Category | Examples | Notes |
|----------|----------|-------|
| **On track** | Iceland (2045), Denmark (2056), Sweden (2076) | High current % + strong growth slope |
| **Beyond 9999** | Saudi Arabia, Qatar, Singapore | Near-zero share and negligible growth |
| **Trend Negative** | Colombia, Sri Lanka | High hydro dependency + demand growth outpacing new build |

> ⚠️ **Model Caveat:** Linear regression ignores the "last mile" difficulty of reaching 100%, weather-driven hydro fluctuations, and future policy shifts. Projections are illustrative, not predictive.

---

## 🛠️ Technologies Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, reshaping |
| `numpy` | Numerical operations |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualisations |
| `scikit-learn` | Linear regression forecasting |

---

## 🚀 Getting Started

**Prerequisites:** Python 3.8+

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/renewable-energy-analysis.git
   cd renewable-energy-analysis
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. Launch the notebook:
   ```bash
   jupyter notebook renewable_energy_analysis.ipynb
   ```

---

## 📈 Key Visualisations

- Distribution histogram of global renewable share with KDE
- Line chart: World renewable share (1965–2022) with 10-year rolling average
- FacetGrid: Per-country time series panels
- Bar chart: Top 10 countries by renewable share (2021)
- Stacked bar chart: Fastest-climbing countries (1990 vs 2021)
- Event correlation chart: Renewable share vs. Kyoto & Paris Agreement dates
- Lollipop chart: Projected year to reach 100% renewables by country

---

## 📝 Notes & Limitations

- The sharp 2020 increase is partly a **COVID anomaly** and may not reflect a sustained structural shift.
- Linear forecasting **does not account** for technology breakthroughs, policy changes, or the increasing difficulty of the final percentage points.
- Countries heavily reliant on hydropower may show **negative trends** due to climate-driven droughts, not actual policy failure.
- Some regions and income-group aggregates are excluded from country-level analysis to avoid skewing results.

---

## 📄 Data Source

Dataset sourced from Kaggle: [Renewable Energy World Wide: 1965–2022](https://www.kaggle.com/datasets/belayethossainds/renewable-energy-world-wide-19652022) by Belayet Hossain DS.

---

*University project — Data Analysis & Visualisation*
