# Global Migration Analysis: Understanding Through Economic & Demographic Lenses

This repository contains the data analytics project for the course **DS25 - Data Analytics** at the **University of Europe for Applied Sciences**. 

## Project Overview
Migration is a deeply human decision driven by opportunity, pressure, crisis, and ambition. This project explores the macroeconomic and demographic factors that drive net migration flows across more than 200 countries over a span of more than two decades (2000–2024). By integrating rich datasets from the World Bank, the project examines how GDP per capita, total population size, and regional/income contexts influence net migration dynamics using exploratory data analysis (EDA), statistical methods, and machine learning techniques.

### Team Members
* **Grisham Tiwari**
* **Suwash Chandra Gautam**
* **Mouhssine Benaali**

**Presented to:** Prof. Dr. Nor Azizah Hitam  
**Date:** July 19, 2025

---

## Datasets
The analysis is powered by the following four World Bank datasets:
1. **World Bank Net Migration (`API_SM.POP.NETM_DS2_en_csv_v2_38276.csv`):** Measures the total number of people moving in or out per year per country.
2. **World Bank Population (`API_SP.POP.TOTL_DS2_en_csv_v2_38144.csv`):** Total historical population data per country.
3. **GDP per Capita (`API_NY.GDP.PCAP.CD_DS2_en_csv_v2_38293.csv`):** Current economic indicator per person (USD) representing economic opportunity.
4. **Metadata (`Metadata_Country_API_SM.POP.NETM_DS2_en_csv_v2_38276.csv`):** Regional and income-group classifications for each country.

---

## Key Methodology & Project Workflow

### 1. Data Cleaning & Structuring
* Reshaped data from wide format to a unified, long country-year panel dataset (2000–2024).
* Normalized the metric by creating **Migration Rate per 1,000 people**:
  $$\text{Migration Rate} = \frac{\text{Net Migration}}{\text{Population}} \times 1000$$
* Handled missing metrics safely via linear interpolation group-by country level and corrected country-metadata alignments.

### 2. Exploratory Data Analysis (EDA)
* **Global Trends:** Identified severe fluctuations in global net migration waves post-2015 and a sharp decline around 2020 due to global pandemic mobility restrictions.
* **Regional & Income Distributions:** Visualized net migrations indicating that North America and High-Income nations systematically act as migration magnets, whereas Sub-Saharan Africa, South Asia, and Low-Income countries experience steady outflows.
* **Economic Pull Factors:** Analyzed the clear log-scale positive correlation between a country's GDP per capita and its attraction for net immigration.

### 3. Clustering & Migration Profiles
Applied **K-Means Clustering** ($K=4$) combined with Principal Component Analysis (PCA) to discover clean behavioral profiles cutting across geographic bounds:
* **Cluster 0 (Sender States):** Medium-income, mid-size populous nations experiencing minor net outflows.
* **Cluster 1 (Magnet Economies):** Rich, advanced economies (e.g., Canada, Germany, Gulf states) drawing continuous labor and skill inflows.
* **Cluster 2 (Swing Giants):** Massively populated nations (e.g., India, China) with stabilized or internally absorbed migrations.
* **Cluster 3 (Wealthy Leavers / Small-State Senders):** Small territories or developing nations facing intensive outward "brain-drain".

### 4. Machine Learning & Feature Importance
* Trained a **Random Forest Regressor** to deduce predictive weights.
* Discovered that **Total Population Size** (demographic pressure) and **GDP per Capita** (economic pull) are the strongest primary indicators driving migration rates globally.

### 5. Predictive Modeling
Tested and evaluated multiple machine learning approaches to forecast the `Migration_Rate_per_1000`:
* **Linear Regression:** $R^2 = 0.179$ (Weak linear capability)
* **Random Forest Regressor:** $R^2 = 0.490$ (Captured complex non-linear nuances)
* **XGBoost Regressor:** $R^2 = 0.498$ (Best overall performer with the lowest Root Mean Squared Error)

---

## Technical Stack & Libraries
The code is built entirely in Python using a Jupyter Notebook workflow utilizing the following essential libraries:
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn`, `xgboost`

## How to Run the Project
1. Clone this repository to your local environment.
2. Ensure all relevant World Bank `.csv` data files are placed in the root directory.
3. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn xgboost`
4. Open and run the Jupyter notebook to reproduce the panels, visualizations, clustering configurations, and model metrics.
