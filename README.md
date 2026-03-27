# Brownfield Detection – Munich

## Overview
This project implements a machine learning framework to identify potential brownfield sites in Munich using Sentinel-2 imagery.

---

## 1. Installation

Install required libraries:

```bash
pip install numpy pandas matplotlib scikit-learn rasterio geopandas

## 2. Data Download

Sentinel-2 data can be downloaded from:
https://scihub.copernicus.eu/

## 3. Preprocessing

Steps performed:

Removal of invalid pixels (NaN values)
Calculation of NDVI and NDBI
Aggregation to 100m grid

## 4. Running the Code

Open the notebook:

Brownfield Detection - Munich.ipynb

Run all cells sequentially from top to bottom.

## 5. Outputs

The code generates:

Sentinel-2 RGB image (Figure 1)
Proxy ground truth map (Figure 2)
Predicted land use map (Figure 3)

## 6. Notes

Labels are proxy-based (NDVI/NDBI thresholds), not real ground truth.
