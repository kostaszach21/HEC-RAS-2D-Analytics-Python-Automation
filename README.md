## Project Overview
This project automates the analysis of HEC-RAS 2D hydraulic simulations using Python. By directly parsing binary output files (`.hdf`), it identifies flood hotspots, calculates hazard metrics based on international safety standards, and applies Machine Learning (DBSCAN) to group high-risk areas—bypassing the need for manual processing in the HEC-RAS GUI.

## Key Features
* **Direct Binary Parsing:** Uses h5py to extract high-resolution Depth and Velocity data directly from binary files for maximum speed.
* **Automated Hazard Classification:** Computes flood risk based on the **Depth $\times$ Velocity** product ($D \times V$).
* **Spatial Clustering (ML):** Implements **DBSCAN** to automatically detect and delineate distinct "Danger Zones" (hotspots).
* **Automated Dashboard:** Generates a complete visualization suite (Hydrographs, Maps, Volume Curves) in a single step.

## Methodology

### 1. Data Extraction
* Loads `.p01.hdf` binary files directly.
* Cleans data by filtering dry cells and handling missing velocity vectors.
* Extracts mesh geometry (coordinates) and hydraulic variables (WSE, Depth, Velocity).

### 2. Risk Calculation
* **Critical Analysis:** Identifies cells with maximum depth and fastest rate-of-rise.
* **Hazard Formula:** Classifies risk levels (Low to Extreme) using the stability criterion: $Risk = Depth \times Velocity$.

### 3. Spatial Clustering 
    * Groups neighboring high-risk cells into defined zones.
    * Provides aggregated statistics (e.g., Max Depth, Area) for each identified cluster.

## Usage

**Prerequisites:** Python 3.x, `h5py`, `numpy`, `pandas`, `scikit-learn`, `matplotlib`.
