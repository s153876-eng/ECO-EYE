# 🌍 إيكو-آي (Eco-Eye) | Smart Sustainable Agriculture & Multi-Source Satellite Monitoring

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://streamlit.io/)
[![NASA Data](https://img.shields.io/badge/Data-NASA%20%7C%20USGS%20%7C%20USDA-blue.svg)](https://earthdata.nasa.gov/)
[![Python](https://img.shields.io/badge/Python-3.10%2B-green.svg)](https://www.python.org/)

**Eco-Eye (إيكو-آي)** is an interactive **Streamlit** geospatial decision-support platform designed for arid and semi-arid agricultural environments (specifically tailored for **Omani farms**). It integrates multi-source Earth observation datasets with spectral band processing and AI-driven agronomy recommendations to detect early crop water stress, soil salinity, and thermal anomalies.

---

## 🔬 Research Question & Scientific Methodology

> *"To what extent does integrating multi-source satellite data (SMAP, ECOSTRESS, GPM, SSURGO, Landsat) with ground-truthing measurements improve the reliability of early plant water-stress detection in Omani farms compared to relying on a single traditional vegetation index (such as NDVI)?"*

### 📡 Data Architecture (5 Core Direct Sources + 3 Derived Spectral Indices)

1. **5 Direct Core Datasets:**
   * **NASA SMAP:** Surface soil moisture ($0\text{--}5\text{ cm}$) for early drought detection.
   * **NASA ECOSTRESS:** Land Surface Temperature ($LST$) & thermal stress hotspots.
   * **NASA GPM & IMERG:** Monthly and cumulative precipitation estimates.
   * **USDA NRCS SSURGO:** Soil drainage classification and water-holding capacity.
   * **NASA/USGS Landsat (8/9):** 30m multispectral imagery for **NDVI** (Normalized Difference Vegetation Index).

2. **3 Indirectly Derived Spectral Indices (Calculated from Landsat Bands in `streamlit_app.py`):**
   * **MSAVI (Modified Soil-Adjusted Vegetation Index):** Eliminates bright sandy soil background noise common in Omani palm and crop farms using `Red` and `NIR` bands.
   * **NDWI (Normalized Difference Water Index):** Detects leaf canopy water stress prior to visible wilting using `NIR` and `SWIR` bands.
   * **NDSI (Normalized Difference Salinity Index):** Identifies surface soil salinization in coastal and inland farms (e.g., Al Batinah) using `Red` and `NIR` ratios.

---

## 📂 Repository Structure

```text
eco-eye-agriculture/
├── streamlit_app.py            # Main Streamlit web application (Maps, NASA API, Spectral Engine, AI Advisor)
├── requirements.txt            # Python dependencies for Streamlit Cloud & local setup
├── README.md                   # Project documentation
├── data/
│   └── oman_farms_sample.csv   # Ground-truthing & multi-source satellite validation dataset for Oman
└── docs/
    ├── Eco-Eye_Complete_Documentation.md
    └── Eco-Eye_Research_Framework.md
```

---

## 🚀 How to Run in Streamlit

### Option 1: Run Locally
1. Clone your repository:
   ```bash
   git clone https://github.com/yourusername/eco-eye-agriculture.git
   cd eco-eye-agriculture
   ```
2. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Launch the Streamlit app:
   ```bash
   streamlit run streamlit_app.py
   ```

### Option 2: Deploy Free on Streamlit Community Cloud
1. Upload `streamlit_app.py`, `requirements.txt`, and `data/oman_farms_sample.csv` to your GitHub repository.
2. Go to [share.streamlit.io](https://share.streamlit.io/), connect your GitHub account, select your repository, and set the main file path to `streamlit_app.py`.
3. Click **Deploy**!