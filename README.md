# NorthStar Urban Mobility — Databases & Analytics Coursework

This repository contains the analytical deliverables for the **University of West London — Databases and Analytics** coursework, applied to the **NorthStar Urban Mobility and Logistics** case study.

NorthStar is a regional UK group operating across transport, last-mile delivery, warehouse dispatch, EV charging, route planning and a mobile customer/driver platform. This project investigates why operational performance is deteriorating, why complaints are rising despite "successful" delivery records, and how the company's data architecture should be redesigned to support better decisions.

## Repository contents

```
.
├── data/                            # Raw NorthStar dataset (9 CSVs + dictionary)
├── notebooks/
│   ├── 01_Section1_SQL_in_R.ipynb   # SQL inside R; cleaning, joins, R viz
│   ├── 02_Section2_Python_Pandas_NumPy.ipynb   # Master frame, stats, pair plots
│   └── 03_Section3_MongoDB_Atlas.ipynb         # NoSQL design, CRUD, indexing
└── docs/
    └── 00_MongoDB_Atlas_Setup.md    # Step-by-step Atlas free-tier setup
```

## How to run

Each notebook can run in Google Colab. The data layer is configurable:

```python
USE_LOCAL = True   # read from Colab's local upload pane
                   # set to False to pull from this repo's raw URLs
```

For Section 3 you also need a MongoDB Atlas free-tier cluster. The full setup walk-through is in `docs/00_MongoDB_Atlas_Setup.md`. Once the cluster is up, paste the connection string when prompted in the notebook (uses `getpass`, so the string is not stored in the file).

## Findings at a glance

1. **Zone vocabulary is inconsistent** across systems (`Airport`, `AIRPORT`, `Ctr` for Central, etc.); cross-table reports are wrong without a normalisation step.
2. **The "completed-but-failed" paradox** is real and quantifiable — a non-trivial share of `OnTime` deliveries have linked complaints. `delivery_status` alone under-states dissatisfaction.
3. **Manual route overrides correlate with failure**, but the relationship is moderated by zone and service type (not pure driver malice).
4. **Hidden cost concentration** — the worst zone × service combinations have negative net contribution once compensation and energy cost are netted off revenue.
5. **A document model fits the case study's nested operational data** (complaints, exceptions, app events) far better than the existing relational schema; indexes on the `journeys` collection cut documents-examined and switch the plan to `IXSCAN`.

## Tech stack

- **R** with `sqldf`, `dplyr`, `tidyr`, `lubridate`, `ggplot2`, `readr`, `scales`
- **Python** with `pandas`, `numpy`, `matplotlib`, `seaborn`, `pymongo`
- **MongoDB Atlas** (M0 free tier)

## Reproducibility

All transformations are deterministic given the input CSVs. There are no random seeds outside the optional `pairplot` jitter. Imputation choices and merge `validate=` constraints are documented inline in each notebook.

## Author

Submitted as Assessment 2 (Coursework, 50%) for *Databases and Analytics*, University of West London.
