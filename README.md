# Advancing Transit Equity for Boston’s Underserved Youth (MIT 8th Annual Policy Hackathon)

Despite significant progress made, transit access in Greater Boston remains uneven, with communities like Chelsea, Roxbury, Dorchester, and Lawrence facing disproportionate access and delays. Such barriers especially impact BIPOC youth who depend on transit for access to educational and enrichment opportunities, reducing social mobility and perpetuating cycles of exclusion. In response to this problem, I propose a latitudinal analysis that draws lessons from proven methods in comparable cities like New York, D.C., and Seattle. 

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

3. Cleaning missing values and inconsistent entries

4. Running summary statistics for each region

5. Computing covariance and correlation between key metrics

---

## 3. Statistical Analysis Framework

The analysis relies on standard sample-based statistics, implemented in Python using both manual formulas and numpy/pandas functions.

### 3.1 Sample Size

For each region,

$$
\begin{array}{c}
N \
\text{ = number of Census block groups}
\end{array}
$$

### 3.2 Sample Mean

For any variable $x$ (for example, poverty ratio or commute-60 ratio):

$$
\bar{x} = \frac{1}{N} \sum_{i=1}^{N} x_i
$$

### 3.3 Sample Variance

$$
s^2 = \frac{1}{N - 1} \sum_{i=1}^{N} (x_i - \bar{x})^2
$$

### 3.4 Sample Standard Deviation

$$
s_x = \sqrt{\frac{1}{N - 1} \sum_{i=1}^{N} (x_i - \bar{x})^2}
$$

### 3.5 Sample Covariance Between Two Variables ($X$ and $Y$)

(Here: $X =$ poverty ratio, $Y =$ commute-60 minute ratio)

$$
\mathrm{cov}(X, Y) = \frac{1}{N - 1} \sum_{i=1}^{N} (x_i - \bar{x})(y_i - \bar{y})
$$

### 3.6 Pearson Product-Moment Correlation Coefficient

$$
r = \frac{\mathrm{cov}(X, Y)}{s_X s_Y}
$$

This coefficient quantifies whether, within a region, higher poverty levels tend to coincide with longer commute burdens.

## 4. Numerical Methods and Python Implementation

The notebook computes all summary statistics manually using:

- numpy.mean(), numpy.var(), numpy.std()

- Custom Python functions replicating the exact formulas above

- Pairwise covariance and correlation using both formulas and numpy.cov() / numpy.corrcoef()

For each region, the script outputs:

- Mean poverty ratio

- Mean commute-60 min. ratio

- Sample variances and standard deviations

- Covariance between poverty and commute burden

- Pearson correlation coefficient r

These statistical indicators allow for direct comparison across cities.

## 5. Key Findings

Based on the current datasets:

- Washington DC and New York City display substantially higher mean poverty ratios (mid-30% range) and extreme commute rates (≈ 38% or higher).

- Boston and Seattle exhibit much lower levels on both metrics (≈ 10% for poverty and long commutes).

- Correlation patterns differ strongly by city:

  - DC and NYC show clear positive correlations between poverty and extreme commute burden.

  - Boston and Seattle show weak or negligible correlations, suggesting more equitable spatial distribution of transit access.

These disparities point to an important question for further research. It is worth investigating
whether transit agencies in Washington, D.C., and New York City differ financially from those in Boston
and Seattle. Examining operating costs, revenue structures, and fare policies may help reveal whether
financial conditions contribute to, or result from, the transit inequities observed.

## 6. Figures 
(Legend: Red - proportion of individuals whose household income is below 100% of the federal poverty threshold, Blue - % of workers whose total commute time is 60 minutes or longer)

- **Boston, MA**
  
![Boston, MA](figures/Boston_MA.png)

- **New York City, NY**

![New York City, NY](figures/NYC_NY.png)


- **Washington D.C.**

![Washington D.C.](figures/Washington_D.C.png)

- **Seattle, WA**

![Seattle, WA](figures/Seattle_WA.png)
