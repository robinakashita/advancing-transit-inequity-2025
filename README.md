# Advancing Transit Equity Through Geospatial and Statistical Analysis (MIT 8th Annual Policy Hackathon)

This repository contains a Python-based statistical and QGIS geospatial analysis of transit inequity across four major U.S. cities: Boston, Washington DC, New York City, and Seattle. Using U.S. Census block-group datasets from 2019 to 2023 and custom demographic GeoPackages that were built for each city, the notebook quantifies poverty levels, extreme commute burden, and the statistical relationships between these variables.

The full analysis is implemented in a single, self-contained Jupyter Notebook:
- `Advancing_Transit_Equity_Robin.ipynb`
  
---

## 1. Research Motivation

Public transportation is a lifeline for millions of U.S. residents, particularly in low-income communities where households may lack reliable access to personal vehicles. Yet many of these same communities face:

- Long commute times,

- Limited transit reliability, and

- Disproportionate socioeconomic barriers.

This project demonstrates how openly available Census data and Python-based statistics can be combined to:

- Measure neighborhood-level poverty and commute-60 ratios,

- Identify structural differences among cities,

- Quantify how strongly poverty correlates with extreme commute burden, and

- Inform equitable transit planning decisions.

The workflow is designed so that future students and researchers can extend it to new regions, metrics, or policy applications.

---

## 2. Data Acquisition and Preprocessing

The notebook utilizes:

- American Community Survey (ACS) block-group-level demographic data from 2019–2023

- Geospatial layers processed using QGIS and exported as custom GeoPackages

- Python tools such as pandas, geopandas, numpy, and matplotlib

Each region’s dataset contains variables such as:

- income_100PercentPoverty_ratio — share of residents living below the poverty line

- workers_60minCommute_ratio — proportion of the labor force with commutes ≥ 60 minutes

- Additional contextual variables (e.g. zero-car households, population density)

Preprocessing steps include:

1. Reading GeoPackages into GeoDataFrames

2. Selecting relevant variables

3. Cleaning NaNs and inconsistent entries

4. Running summary statistics for each region

5. Computing covariance and correlation between key metrics
