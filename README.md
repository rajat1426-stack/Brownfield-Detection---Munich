# Brownfield Detection – Munich

## Overview
This project implements a machine learning framework to identify potential brownfield sites in Munich using Sentinel-2 imagery.

---

## 1. Installation

Python version: 3.10+

Install required libraries:

```bash
pip install numpy pandas matplotlib scikit-learn rasterio geopandas

## 2. Data Download

Sentinel-2 data can be downloaded from:
https://scihub.copernicus.eu/

Example dataset:

Tile: T32UPU (Munich region)
Product: Sentinel-2 Level-2A (surface reflectance)

Bands used:

B2 (Blue)
B3 (Green)
B4 (Red)
B8 (Near-Infrared)

## 3. Preprocessing

Steps performed:

Removal of invalid pixels (NaN values)
Calculation of NDVI (Normalized Difference Vegetation Index)
Calculation of NDBI (Normalized Difference Built-up Index)
Aggregation to 100m grid resolution

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
The model learns the labeling rule rather than independent spatial patterns.

## 7. Reproducibility

All results in the report can be reproduced by running the notebook with the specified Sentinel-2 data.

## 8. License

This project is licensed under the Apache 2.0 License.
