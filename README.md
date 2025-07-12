# Wetland Detection and Mapping using Python API

## 🌍 Project Overview
Wetlands are complex and dynamic ecosystems that are often partially covered by vegetation, making it challenging to delineate water bodies using standard water indices. This project presents a method for wetland mapping and waterbody extraction using Landsat 8 SR imagery and spectral band-based thresholding, implemented through the xee and geemap Python APIs.

The analysis was performed over Vankalai Wetland, a Ramsar site in the Mannar District, Sri Lanka.

## 🔍 Key Objective
Use band thresholding (NIR & SWIR2) to improve delineation of wetland water bodies, especially under vegetative cover.



| NDWI (Low performance in vegetated areas) | Final Wetland Water Delineation (Improved) |
| ----------------------------------------- | ------------------------------------------ |
| <img width="745" height="615" alt="Screenshot (249)" src="https://github.com/user-attachments/assets/b36ed49c-5dd9-40cc-a90c-8aa3e1cc76be" />                  | <img width="712" height="594" alt="Screenshot (250)" src="https://github.com/user-attachments/assets/79f8c47f-82d6-4d25-92b1-9e2f2fe9ae43" />




## 🧠 Methodology
1. Data Preparation
- Load Landsat 8 SR imagery for 2020–2024 over a user-drawn roi (Region of Interest).
- Filter by cloud cover < 45%.
- Compute mean composite.

2. Scaling Surface Reflectance
    #### Landsat SR values are scaled:
    <img width="528" height="52" alt="image" src="https://github.com/user-attachments/assets/504aaae3-28ee-492e-8552-e21b32f58e80" />

3. Vegetation and Water Indices
NDVI = (NIR - RED) / (NIR + RED)
→ Indicates vegetation cover.

NDWI = (GREEN - NIR) / (GREEN + NIR)
→ Helps identify surface water but may struggle in vegetated wetlands.

4. Wetland Water Delineation via Spectral Thresholding
- Many wetlands are missed by NDWI due to vegetation.
- Pixels are classified as potential wetland water when:
    NIR ≤ 0.1735
    SWIR2 ≤ 0.1035

Two logic modes tested:
- AND condition: High confidence in water detection.
- OR condition: Broader detection, potentially including more shallow/vegetated water.

.

## 📌 Notes
- Although this method was applied to wetlands, the band-thresholding logic can be adapted to any land cover type for water detection.
- You can refine thresholds or add SAVI, MNDWI for more complex scenes.
- Landsat’s 30m resolution is suitable for medium-scale wetlands; Sentinel-2 or SAR could improve results for narrow or fragmented wetlands.







