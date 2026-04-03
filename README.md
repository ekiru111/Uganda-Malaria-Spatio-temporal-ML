# Predictive Modeling and Spatio-Temporal Simulation of Malaria Outbreaks in Uganda

## Author
**Name:** Ekiru Ernest Ochepa  
**Program:** Kujenga AI/ML Course

---

## Objective
This research develops a predictive machine learning model to identify malaria risk factors and forecast malaria outbreaks across Uganda. The project integrates multiple data sources including demographic surveys, household characteristics, geographic information, and satellite-derived environmental variables to build a comprehensive spatio-temporal analysis of malaria transmission patterns.

---

## Key Research Components

### 1. **Data Sources**
- **UDHS Malaria Survey Data (UGPR7IFL.DTA):** Individual-level malaria test results using RDT (Rapid Diagnostic Tests)
- **Household Recode Data (UGHR7IFL.DTA):** Household wealth, housing materials, and mosquito control interventions (IRS)
- **Geographic Data (UGGE7IFL.shp):** GPS coordinates and altitude of survey clusters
- **Environmental Data (Google Earth Engine):** Precipitation and temperature variables (lagged by 2 months)
- **Administrative Boundaries:** Uganda district and regional shapefiles for spatial analysis

### 2. **Data Processing Pipeline**
- **Target Variable:** Malaria RDT test results (positive/negative binary classification)
- **Data Cleaning:** Extracted 7,787 individual records with complete malaria test results from 45,767 total respondents
- **Feature Integration:** Merged individual, household, geographic, and environmental datasets using cluster and household identifiers
- **Variable Transformation:** Converted Century Month Code (CMC) dates to calendar years/months for temporal analysis

### 3. **Predictor Variables**
- **Demographic:** Age, sex, household size
- **Socioeconomic:** Wealth index (5-category scale from poorest to richest)
- **Housing Characteristics:** Floor material, wall material, roof material
- **Behavioral:** Bed net usage (LLIN and any net types), ITN access
- **Environmental:** Rainfall (2-month lag), Temperature (2-month lag), Altitude
- **Interventions:** Household IRS (Indoor Residual Spraying) in last 12 months
- **Geographic:** Region, urban/rural classification, GPS coordinates

### 4. **Data Integration Methodology**
- Linked individual malaria test results to household-level socioeconomic data
- Attached geographic coordinates and altitude to survey clusters
- Extracted Google Earth Engine environmental variables at survey point locations
- Handled missing satellite data through mean imputation for precipitation and temperature

---

## Dataset Summary
- **Total Records:** 7,787 children tested for malaria
- **Geographic Coverage:** All regions and districts of Uganda
- **Temporal Period:** Survey conducted across multiple years with 2-month lagged environmental variables
- **Class Distribution:** Classified individuals as malaria-positive or malaria-negative based on RDT results

---

## Expected Outcomes
- Predictive model to identify high-risk populations for malaria infection
- Spatio-temporal visualization of malaria risk across Uganda's administrative regions
- Quantified impact of socioeconomic factors, environmental conditions, and interventions on malaria transmission
- Supporting data for targeted malaria prevention and control strategies

---

## Project Structure
- `Modeling_malaria.ipynb` - Main analysis and data pipeline
- `Pure_SIR_model.ipynb` - Epidemiological compartmental model
- `Uganda_Malaria_Env_Full.csv` - Processed dataset with environmental features
- `malaria_points_for_gee.csv` - Input file for Google Earth Engine extraction
- `uga_admin_boundaries.shp/` - Uganda administrative boundary shapefiles
- Supporting DHS data files and household recode datasets
