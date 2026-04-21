# CIVE 202: Project 4 - Natural Disaster Risk Sensitivity Analysis

**Group 09** **Client:** Risk Averse, LLC  
**Analyzed States:** Colorado & Minnesota  

## Project Overview
This repository contains a sensitivity analysis of the Federal Emergency Management Agency's (FEMA) National Risk Index (NRI). The primary objective of this project is to investigate potential categorical bias within the FEMA NRI framework, which traditionally relies heavily on raw property value (Expected Annual Loss) to determine disaster risk. 

By integrating Centers for Disease Control and Prevention (CDC) Social Vulnerability Index (SVI) data, this project proposes a custom, human-centric risk model. This new model demonstrates how prioritizing social vulnerability and lack of community resilience fundamentally shifts the geographical distribution of "High Risk" Census tracts, highlighting ethical implications for future mitigation funding.

## Repository Structure
* **`CIVE202_Spring2026_G09_Project4_Python.ipynb`**: The primary Jupyter Notebook containing all data cleaning, merging, mathematical modeling, and visualization code.
* **`Colorado_NRI.csv` & `Minnesota_NRI.csv`**: Filtered FEMA National Risk Index datasets.
* **`Colorado.csv` & `Minnesota.csv`**: CDC Social Vulnerability Index (SVI) datasets.
* **`NRIDataDictionary.csv`**: Reference dictionary for the FEMA NRI metrics.
* **`Shapefiles`**: Directory containing the `.shp`, `.dbf`, `.shx`, and `.prj` files required for GeoPandas rendering.

## Methodology: The Proposed Risk Model
This analysis replaces FEMA's standard additive risk scoring with a **Multiplicative Risk Model**. To eliminate the bias of raw property value overshadowing vulnerable populations, all variables were Min-Max normalized (0 to 1 scale) and calculated at the Census Tract level:

**`Proposed Risk = (Normalized EAL) × (Normalized SVI) × (Lack of Resilience)`**

*Note: "Lack of Resilience" was calculated as `1 - Resilience_norm` to ensure a high capacity to recover mathematically lowers the overall risk score.*

## Key Findings
1. **Categorical Bias Identified:** The sensitivity analysis revealed a systemic bias in the standard FEMA NRI against rural and lower-income communities. 
2. **Shift in Vulnerability:** When applying the proposed multiplicative model, tracts previously deemed "Low Risk" by FEMA (due to low property values) spiked to the highest percentiles due to intersecting high social vulnerability and low resilience.
3. **Geospatial Proof:** The generated GeoPandas maps visually confirm this shift, prioritizing regions like Southern Colorado and Northern Minnesota over wealthier urban/resort centers.

## How to Run
To reproduce this analysis locally:
1. Clone this repository.
2. Ensure you have the following Python packages installed: `pandas`, `numpy`, `matplotlib`, `seaborn`, and `geopandas`.
3. Verify that the `Shapefiles` directory is in the same working directory as the Jupyter Notebook.
4. Run all cells in `CIVE202_Spring2026_G09_Project4_Python.ipynb`.
