# Predictive Modeling and Spatio-Temporal Simulation of Malaria Outbreaks in Uganda

## Author
**Name:** Ekiru Ernest Ochepa  
**Program:** Kujenga AI/ML Course

---

## Objective

### **Overall Objective**
This research develops a predictive machine learning model to identify malaria risk factors and forecast malaria outbreaks across Uganda. The project integrates multiple data sources including demographic surveys, household characteristics, geographic information, and satellite-derived environmental variables to build a comprehensive spatio-temporal analysis of malaria transmission patterns.

### **Specific Objective**
1. Develop a predictive machine learning model to identify malaria risk factors
2. Forecast malaria outbreaks across Uganda
3. Build a comprehensive spatio-temporal analysis of malaria transmission patterns

---

## Results

### **Model Development and Performance**
A hybrid ensemble approach was employed, combining a Random Forest classifier with XGBoost after addressing class imbalance through SMOTE (Synthetic Minority Over-sampling Technique).

##### **Model Performance Metrics:**

***Sensitivity (Recall):*** 22.7% - The model identifies approximately 1 in 4 malaria-positive individuals

***Specificity:*** 95.7% - The model correctly identifies 96 out of 100 malaria-negative individuals

***Overall Accuracy:*** 87.9% - High accuracy driven by the high specificity

***Precision:*** 38.5% - When the model predicts a positive case, it is correct 38.5% of the time

***AUC-ROC:*** Strong discrimination capability between positive and negative malaria cases

***The confusion matrix revealed:***

- True Negatives: 1,310 (correctly identified negative cases)
- False Positives: 59
- False Negatives: 126
- True Positives: 37

***Data Quality:*** Analysis was conducted on 7,787 individual children across Uganda with complete malaria RDT (Rapid Diagnostic Test) results and comprehensive socioeconomic, environmental, and geographic data.

### **Top 4 Malaria Risk Drivers (Feature Importance)**
The XGBoost model identified the following top factors influencing malaria risk in Uganda:

***Housing Construction - Thatch/Palm Leaf Roofs (0.31 importance)*** - The most dominant risk factor; homes with traditional thatch roofing showed dramatically elevated malaria risk

***Wealth Index - Richest Households (-0.07 importance)*** - Protective factor; wealthier households demonstrated significantly lower infection rates

***Housing Construction - Iron Sheet Roofs (0.06 importance)*** - Moderate protective effect

***Household Insecticide Spraying (IRS) (0.05 importance)*** - Protective intervention; households sprayed in the last 12 months showed reduced malaria risk

***Key Finding:*** Housing quality (particularly roof material) emerged as the strongest predictor of malaria infection, followed by household wealth and regional geography.

### **Primary Objective 2: Forecast Malaria Outbreaks Across Uganda**

Spatio-Temporal Outbreak Dynamics

Regional Risk Stratification (by malaria prevalence):

- **Very High Risk (>20%):** Karamoja region (32.1%), Busoga region (21.4%)
- **High Risk (15-20%):** Lango region (15.9%), West Nile region (19.2%)
- **Moderate Risk (10-15%):** Acholi region (14.7%), North Buganda region (11.4%), Bunyoro region (10.2%)
- **Low Risk (<10%):** Teso region (8.9%), Kampala region (0.4%), Ankole region (2.2%), Kikezi region (0.3%), South Buganda region (1.0%)

![Malaria risk map of uganda](malaria_risk_map.png)

#### **Outbreak Peak Timing:**
Two complementary analyses were conducted:

SEIR (Susceptible-Exposed-Infectious-Recovered) Model Dynamics:

- **Peak sick children (unmitigated):** 2,978 children on day 40 post-outbreak initiation
- **Outbreak duration:** Approaximately 200 days from initial cases to disease fadeout
- **R₀ (basic reproduction number) ≈ 1.4, indicating moderate transmission potential**

### **Bed Net Distribution Intervention Analysis:**

- **Baseline peak cases:** 2,978 children (day 40)
- **With mass LLIN distribution:** 2,490 children (day 50)
- **Net reduction:** 488 fewer cases (16% reduction in peak cases)
- **Timing shift:** Peak occurrence delayed by 10 days, allowing healthcare systems additional preparation time

- **Duration flattened:** Outbreak duration extended slightly, reducing system burden

### **Primary Objective 3: Build a Comprehensive Spatio-Temporal Analysis of Malaria Transmission Patterns**

#### ***Geographic Risk Mapping***

#### **High-Risk Hotspots Identified:**
The spatial analysis revealed distinct malaria transmission zones:

#### **1. Eastern Corridor (Karamoja-Busoga-Lango):** The highest burden region, accounting for nearly 70% of malaria cases. This zone exhibits:

- High temperature and rainfall supporting vector breeding
- Lower wealth indices and limited accessibility to interventions
- Traditional housing with limited mosquito barriers

#### **2. Western Zone (West Nile-Bunyoro):** Secondary but significant transmission zone (19-20% prevalence) with:

- ***Equatorial climate conditions favoring mosquito populations***
- ***Limited bed net coverage in rural areas***

#### **3. Central Region (Kampala-North Buganda):** Substantially lower transmission (<2% in urban centers), likely due to:

- Higher urbanization rates and household wealth
- Better access to healthcare and preventive measures
- Improved housing infrastructure

### **Environmental and Demographic Patterns**

**Climate-Malaria Linkage:**

- **Rainfall impact:** 2-month lagged rainfall showed significant influence on transmission (correlation: -0.57 with temperature, indicating interdependent effects)
- **Seasonal dynamics:** The model captures the delayed relationship between peak rainfall and case emergence, critical for early warning systems
Age-Risk Distribution:

Median age of positive cases: ~39 months
Median age of negative cases: ~29 months
Older children showed higher infection rates, suggesting acquired partial immunity dynamics

Altitude Protection:

Strong negative correlation observed: higher altitude areas (>1,500m) showed 40-50% lower malaria prevalence
South-central highlands (Ankole, South Buganda) at elevations >1,000m demonstrate protective altitude effect

### **Intervention Coverage Assessment**

Current Protection Status:

- Bed Net Usage: Only 9-15% of surveyed children reported sleeping under LLINs
- IRS Coverage: 3-8% of households sprayed in the 12 months preceding the survey
- Gap: Massive protection gap exists between current coverage and minimum targets for malaria control (>80% LLIN coverage recommended by WHO)

### **Summary of Key Findings**
- Housing quality is the strongest modifiable risk factor, with immediate policy implications for housing improvement programs

- Regional disparities are stark, with Karamoja bearing 32× the malaria burden of Kigezi region

- Intervention potential is substantial: Achieving 80% LLIN coverage could theoretically reduce peak cases by 16-20% and provide valuable time for health system response

- Wealth remains protective: Socioeconomic development and targeted assistance to poorest households could significantly reduce transmission


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
