# Mental Health Care Accessibility Explorer

**Interactive Web Application for County-Level Mental Health Care Access Analysis**

This repository contains an interactive web application that visualizes and analyzes mental health care accessibility across U.S. counties using a two-dimensional framework of availability and affordability.

## Overview

Access to mental health care encompasses two critical dimensions:

1. **Availability** - The local supply of mental health providers relative to population size
2. **Affordability** - The financial burden of initiating psychotherapy relative to household economic capacity

This application provides interactive tools to explore these dimensions through county-level indices, revealing geographic patterns and socioeconomic relationships that shape mental health care access in the United States.

## Data Sources

The application integrates multiple authoritative data sources:

- **Psychology Today Directory** - Mental health provider information (deduplicated listings)
- **U.S. Census Bureau Population Estimates Program** - County population data (July 1, 2024)
- **American Community Survey (ACS)** - Median household income estimates
- **Economic Policy Institute (EPI) Family Budget Calculator** - Locally specific living costs (housing, food, transportation, childcare, healthcare, taxes, and other necessities)
- **USDA Economic Research Service** - Rural-Urban Continuum Codes (RUCC)
- **National Neighborhood Data Archive (NaNDA)** - County-level presidential election results

## Index Construction

### Availability Index (AVI)

The Availability Index measures the density of mental health providers relative to county population:

```
AVI = (Number of Providers / Population) × 100,000
```

The AVI represents the number of providers per 100,000 residents. For example, an AVI of 100 indicates that a county has 100 listed providers for every 100,000 people in its population. Higher AVI values indicate greater service availability.

### Affordability Index (AFI)

The Affordability Index estimates the baseline financial burden of accessing psychotherapy based on posted cash session fees and local economic conditions:

```
AFI = (10 × Median Fee) / Disposable Income × 100
```

Where:
```
Disposable Income = Median Household Income − Living Cost
```

**Components:**
- **Treatment cost** - Median posted session fee multiplied by ten, representing a standardized benchmark course of initial care
- **Disposable income** - Financial capacity after accounting for essential living expenses
- **Living costs** - Estimated using the EPI Family Budget Calculator for locally specific costs

The AFI is expressed as a percentage. For example, an AFI of 3% indicates that ten psychotherapy sessions represent 3% of a household's median disposable income in that county. Higher AFI values indicate higher financial burden (lower affordability).

## Distributional Adjustment

To ensure robust statistical analysis and improve visualization:

- **AFI values** are winsorized at the 5th and 95th percentiles
- Counties with negative disposable income (where living costs exceed median household income) are assigned the 95th percentile value, representing the highest financial burden
- Extreme values exist in the raw data; refer to the data source for complete information
- Winsorization reduces the influence of outliers while maintaining the overall distribution

## Data Categorization

Both the Availability Index (AVI) and Affordability Index (AFI) are grouped into quintile-based categories:

- **Low** (0-20th percentile)
- **Low Average** (20-40th percentile)
- **Average** (40-60th percentile)
- **Above Average** (60-80th percentile)
- **High** (80-100th percentile)

These categories represent a county's relative position within the national distribution of each index.

### Important Note on AFI Category Interpretation

The Affordability Index (AFI) is mathematically defined as a burden-based measure, where higher AFI values indicate higher financial burden and lower affordability. However, for the purposes of the interactive map, **AFI categories are reversed in interpretation** so that color meanings are consistent with the Availability Index (AVI).

**Specifically:**
- Counties in the **"High"** AFI category represent counties with *higher affordability* (lower financial burden)
- Counties in the **"Low"** AFI category represent counties with *lower affordability* (higher financial burden)

This inversion is applied only at the visualization layer to ensure that darker or "higher" color categories consistently represent more favorable access conditions across both indices.

### AVI Interpretation

The Availability Index (AVI) follows standard interpretation: higher AVI values and higher AVI categories indicate greater provider availability per capita.

## Dual Burden Classification

Counties are classified based on their simultaneous position on both dimensions:

- **Low-Low** - Low availability AND low affordability (dual burden)
- **Low-High** - Low availability but high affordability
- **High-Low** - High availability but low affordability
- **High-High** - High availability AND high affordability

This classification reveals counties facing compounded barriers to care versus those with relative advantages on both dimensions.

## Interactive Features

The application includes three main tools:

### 1. Interactive Accessibility Map ([map.html](map.html))
- Visualize county-level mental health care affordability (AFI) and availability (AVI) across the United States
- Filter by state and toggle between AFI/AVI metrics
- Hover over counties for detailed information
- Download high-resolution PNG figures for publication

### 2. Variable Relationship Explorer ([explorer.html](explorer.html))
- Examine correlations between demographic, economic, and political variables with mental health care accessibility metrics
- Interactive scatter plots with trend lines
- Explore relationships between income, rurality, political preferences, and access
- Download figures with custom variable selections

### 3. Affordability Scenario Calculator ([calculator.html](calculator.html))
- Model different insurance payment scenarios (copays, deductibles, sliding scale)
- Adjust number of therapy sessions to see impact on affordability
- Understand how out-of-pocket costs vary across counties
- Compare cash payment, insurance copay, deductible, and sliding scale fee scenarios
- Download scenario-specific figures

## Interpretation Guidance

When interpreting the visualizations:

- **Geographic patterns** - Identify regions with systematic access barriers or advantages
- **Socioeconomic relationships** - Explore how income, rurality, and other factors correlate with accessibility
- **Payment scenarios** - Understand how different insurance structures affect affordability across counties
- **Dual burden areas** - Focus attention on counties facing both low availability and low affordability

## Purpose

This application supports:

- **Research and analysis** of mental health care accessibility patterns
- **Policy planning** to identify underserved areas
- **Educational purposes** to understand geographic health disparities
- **Publication-quality figures** for academic manuscripts

## Access

The application is deployed via GitHub Pages and can be accessed at:
[https://anonymousforreview23-ctrl.github.io/accessibility_map/](https://anonymousforreview23-ctrl.github.io/accessibility_map/)

## Citation

If you use this application or data in your research, please cite:

**Park, J., Kim, H. R., Duffy, R., Vogel, D., Keum, B. T., Lee, S., & Tomé, N. (2026). Two Dimensions of Access: Availability and Affordability of Mental Health Care Across the U.S. (Software). Zenodo. https://doi.org/10.5281/zenodo.19392686**

---

**Mental Health Care Accessibility Explorer** © 2026
Anonymized Repository for Manuscript Review
