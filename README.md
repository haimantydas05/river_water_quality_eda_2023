
INDIA RIVER WATER QUALITY — EDSA & GEOSPATIAL ANALYSIS (2023)
================================================================

An end-to-end Exploratory Data Analysis (EDA) of India's river
water quality monitoring data for 2023, combining Python-based
data science with geospatial visualization.

----------------------------------------------------------------
PROJECT OVERVIEW
----------------------------------------------------------------
India's river systems face increasing stress from industrial
discharge, agricultural runoff, and urban sewage. This project
processes official water quality monitoring data to uncover
state-wise pollution patterns, detect anomalous stations, and
visualize findings on a choropleth map of India.

Data source: Central Pollution Control Board (CPCB)
             River Water Quality Data 2023

----------------------------------------------------------------
PROJECT STRUCTURE
----------------------------------------------------------------
river_water_quality_eda/
|
|-- river_water_quality_eda.ipynb   Main analysis notebook
|-- River water_quality_2023.csv    Input dataset
|-- INDIA_STATES.geojson            India state boundaries
|-- india_water_quality_map.png     Output choropleth map


----------------------------------------------------------------
WORKFLOW
----------------------------------------------------------------

Phase 1 — Data Loading & First Look
  - Loaded the CSV dataset using pandas
  - Inspected column data types and initial structure

Phase 2 — Data Cleaning & Preprocessing
  - Dropped null/junk rows (missing Location or State)
  - Cleaned State column formatting
  - Removed incomplete columns (Fecal_Streptococci)
  - Converted all measurement columns to numeric types

Phase 3 — Exploratory Data Analysis
  - Count of unique states in the dataset
  - Number of monitoring stations per state
  - Descriptive statistics for key parameters:
    pH, DO, BOD, Conductivity, Nitrate, Fecal Coliform

Phase 4 — Visualizations
  - Bar chart: Average pH Max by state
  - Bar chart: Average DO Min by state
  - Bar chart: Average BOD Max by state
  - Correlation heatmap across all water quality parameters

Phase 5 — Anomaly Detection
  - pH anomaly   : pH_Min < 6.5 OR pH_Max > 8.5
  - DO anomaly   : DO_Min < 5 mg/L
  - BOD anomaly  : BOD_Max > 3 mg/L
  - State-wise BOD anomaly counts
  - Top 10 most polluted monitoring locations

Phase 6 — Geospatial Mapping
  - Loaded India state boundaries from GeoJSON (geopandas)
  - Merged anomaly counts with spatial data
  - Choropleth map of BOD anomalies by state
  - Saved as high-resolution PNG (dpi=300)

----------------------------------------------------------------
KEY PARAMETERS & THRESHOLDS
----------------------------------------------------------------

Parameter          Unit          Anomaly Threshold
-------------------------------------------------
pH                 —             < 6.5 or > 8.5
Dissolved Oxygen   mg/L          < 5
BOD                mg/L          > 3
Conductivity       uS/cm         —
Nitrate            mg/L          —
Fecal Coliform     MPN/100mL     —
Total Coliform     MPN/100mL     —

----------------------------------------------------------------
TECH STACK
----------------------------------------------------------------

pandas         Data loading, cleaning & EDA
numpy          Numerical operations
matplotlib     Bar charts & choropleth map
seaborn        Correlation heatmap
geopandas      Spatial data handling & merging
folium         Interactive mapping (optional)
mapclassify    Map classification schemes

----------------------------------------------------------------
HOW TO RUN
----------------------------------------------------------------

1. Clone or download this repository

2. Install dependencies:
   pip install pandas numpy matplotlib seaborn geopandas folium mapclassify

3. Open the notebook:
   jupyter notebook river_water_quality_eda.ipynb

----------------------------------------------------------------
KEY FINDINGS
----------------------------------------------------------------

- Several states showed BOD levels exceeding 3 mg/L,
  indicating significant organic pollution in river systems

- DO levels below 5 mg/L at multiple stations signal
  stress for aquatic ecosystems

- Strong correlation between BOD, Fecal Coliform and
  Total Coliform — consistent with sewage contamination

- States with denser urban/industrial activity showed
  higher anomaly counts across parameters

----------------------------------------------------------------
AUTHOR
----------------------------------------------------------------

Haimanty
GIS Associate
PG Diploma in Geoinformatics — Jadavpur University
BSc Geography — WBSU

Skills: GIS, Remote Sensing, Python, Google Earth Engine,
        GeoPandas, Spatial Analysis

----------------------------------------------------------------
LICENSE
----------------------------------------------------------------

This project is open-source under the MIT License.

================================================================
