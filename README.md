# Brownfield Detection – Munich

## Overview
This project implements a spatially-aware machine learning framework to identify potential brownfield sites in Munich using Sentinel-2 multispectral imagery.

A Convolutional Neural Network (CNN) is used to capture spatial patterns in land-use, followed by spectral post-processing (NDVI-based refinement) to improve classification accuracy and interpretability.

---

## 1. Installation

Python version: 3.10+

Install required libraries:

```bash
pip install numpy pandas matplotlib scikit-learn rasterio geopandas torch scipy
```

---

## 2. Data Download

Sentinel-2 data can be downloaded from:
https://scihub.copernicus.eu/

Example dataset:

- Tile: T32UPU (Munich region)  
- Product: Sentinel-2 Level-2A (surface reflectance)

Bands used:

- B2 (Blue)  
- B3 (Green)  
- B4 (Red)  
- B8 (Near-Infrared)  

---

## 3. Preprocessing

The following preprocessing steps are applied:

- Removal of invalid pixels (NaN handling)
- Patch extraction (15×15) for CNN input
- Feature normalization (mean–std scaling)
- Generation of RGB composite for visualization

Additionally, NDVI is computed for post-processing:

\[
NDVI = \frac{B8 - B4}{B8 + B4}
\]

---

## 4. Model

A Convolutional Neural Network (CNN) is trained using spatial patches to capture neighborhood context.

Key characteristics:

- Input: 15×15 patches (4 spectral bands)
- Architecture: Convolutional layers + fully connected layers
- Training: Class-balanced sampling
- Framework: PyTorch

The CNN predicts land-use classes:

- Built-up
- Vegetation
- Brownfield (proxy class)

---

## 5. Post-processing

To improve prediction quality:

- NDVI-based refinement is applied:
  - High NDVI → Vegetation
  - Low NDVI → Built-up
  - Intermediate NDVI → Brownfield proxy

- Median filtering (3×3) is used to:
  - Reduce noise
  - Improve spatial coherence

---

## 6. Running the Code

Open the notebook:

```
Brownfield Detection - Munich.ipynb
```

Run all cells sequentially from top to bottom.

---

## 7. Outputs

The code generates:

- **Figure 1:** Sentinel-2 RGB image  
- **Figure 2:** Proxy ground truth map (OSM-based)  
- **Figure 3:** CNN + Spectral Hybrid Land Use Map  

---

## 8. Notes

- Labels are derived from OpenStreetMap land-use polygons and represent proxy ground truth.
- Brownfield areas are approximated as transitional zones between built-up and vegetation.
- The CNN captures spatial structure, while NDVI-based refinement improves class separation.
- Results depend on the quality of proxy labels and may not represent exact real-world brownfield locations.

---

## 9. Reproducibility

All results in the report can be reproduced by:

1. Downloading Sentinel-2 data for Munich
2. Running the notebook with the provided pipeline
3. Using the same patch size and preprocessing steps

---

## 10. License

This project is licensed under the Apache 2.0 License.
