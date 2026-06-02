# CMS National Hospital Performance Audit

> **A data science investigation into the relationship between hospital spending and care quality across the US healthcare landscape.**

---

## Overview

This project acts as a consulting analysis for a major health insurance provider seeking to answer a critical question:

> *Are we paying more for higher-quality care, or are cost and quality entirely decoupled in the current US hospital landscape?*

Using publicly available data from the **Centers for Medicare & Medicaid Services (CMS)**, the analysis merges, cleans, and visualizes three hospital-level datasets to uncover patterns in spending, complications, and regional healthcare value.

**Short answer:** Cost and quality are largely decoupled. Paying more does not guarantee better care.

---

## Project Structure

```
├── notebook.ipynb              # Main analysis notebook (all phases)
├── requirements.txt            # Python dependencies
├── data/                       # Auto-generated on first run (downloaded from CMS)
│   ├── Hospital_General_Information.csv
│   ├── Medicare_Hospital_Spending_Per_Patient-Hospital.csv
│   └── Complications_and_Deaths-Hospital.csv
└── README.md
```

---

## Methodology

The project is split into three phases:

### Phase I — The Unified View (Merging)
- Downloads and extracts the CMS dataset directly from the source
- Loads three separate CSV files into dedicated DataFrames with appropriate type enforcement (e.g. preserving leading zeros in Facility IDs)
- Filters the complications file to the `Hybrid_HWM` mortality measure
- Performs sequential left-outer merges using `Facility ID` as the primary join key, with row-count auditing at each step

### Phase II — The "Janitor" Protocol (Cleaning & Encoding)
- Uses regex to replace CMS placeholder strings (`"Not Available"`, `"Number of Cases Too Small"`) with `NaN`
- Casts score and rating columns to numeric types
- Validates all Facility IDs for correct 6-character length
- Consolidates granular `Hospital Ownership` categories into four logical groups (Government, Voluntary Non-Profit, Proprietary, Other) and applies numerical encoding for visualization

### Phase III — Engineering Insight (Visualization)
Three analytical questions are answered with supporting charts and commentary:

**Q1 — Cost Distribution:** What is the spread of Medicare Spending Per Beneficiary (MSPB) scores across the country, and where are the extreme outliers?

**Q2 — The Value Gap:** Is there a visible relationship between hospital spending and complication rates? Does hospital ownership type explain any of the variance?

**Q3 — Geographic Density:** Which states deliver the worst and best value, measured by a composite payment-to-quality ratio?

---

## Key Findings

<img width="1384" height="778" alt="image" src="https://github.com/user-attachments/assets/0fc272c4-34ab-40ba-8d20-d202df0ec0f9" />

**1. The "Value" Quadrant is densely populated**
Many hospitals — primarily Voluntary Non-Profit institutions — achieve *below-average spending and below-average complication rates* simultaneously, proving that high quality does not require high cost.

**2. The "Worst" Quadrant exists**
A meaningful cluster of hospitals, disproportionately represented by for-profit (Proprietary) facilities, combine *above-average spending with above-average complication rates* — the worst possible value outcome.

<img width="1595" height="644" alt="image" src="https://github.com/user-attachments/assets/96613e40-7341-41d6-8fa9-8076d11bfcd3" />

**3. Geographic polarization is stark**
Using the composite ratio `MSPB_score × Complications_score` (higher = worse value):

| Tier | States | Avg Ratio |
|---|---|---|
| Best value | Hawaii, Minnesota, Alaska, Oregon, Washington | 3.38 – 3.59 |
| Worst value | Mississippi, Louisiana, Arkansas, Tennessee, Alabama | 4.48 – 4.89 |

State-level averages mask significant facility-level variance, but a clear regional pattern emerges: the Deep South consistently underperforms on healthcare value.

---

## Setup & Installation

> **Note:** Please use the provided `requirements.txt` to set up a virtual environment before running the notebook.

```bash
# 1. Clone the repository
git clone https://github.com/your-username/cms-hospital-audit.git
cd cms-hospital-audit

# 2. Create and activate a virtual environment
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch the notebook
jupyter notebook notebook.ipynb
```

The dataset is fetched automatically at runtime from the CMS portal — no manual download is needed.

---

## Dependencies

Key libraries used in this project:

| Library | Purpose |
|---|---|
| `pandas` | Data loading, merging, cleaning |
| `numpy` | Numeric operations, encoding |
| `matplotlib` / `seaborn` | Static charts (histogram, boxplot, scatter) |
| `plotly` | Interactive choropleth maps |
| `requests` / `zipfile` | Automated dataset download |
| `re` / `gc` | Regex cleaning, memory management |

See `requirements.txt` for full version-pinned dependencies.

---

## Data Sources

All data sourced from the **CMS Care Compare** public portal:

- `Hospital_General_Information.csv` — Hospital identifiers, type, ownership, and star ratings
- `Medicare_Hospital_Spending_Per_Patient-Hospital.csv` — MSPB-1 scores per facility
- `Complications_and_Deaths-Hospital.csv` — `Hybrid_HWM` hybrid mortality measure per facility

---

## Conclusion

> **Price and performance do not move together in the current US system.**

The empirical evidence across all three phases consistently points to a decoupling of cost and quality. Hospital ownership type, geographic region, and institutional structure are stronger predictors of patient outcomes than spending level alone. For a health insurance provider, this signals that higher reimbursements to high-cost hospitals are not justified on quality grounds without facility-specific evidence.
