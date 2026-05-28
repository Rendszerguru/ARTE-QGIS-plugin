# ARTE - Arma Reforger Terrain Exporter (QGIS Plugin)

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest)
[![QGIS](https://img.shields.io/badge/QGIS-3.x-green.svg)](https://qgis.org/)
[![Engine](https://img.shields.io/badge/Engine-Enfusion%20(Arma%20Reforger)-orange.svg)](https://reforger.armaplatform.com/)
[![License](https://img.shields.io/badge/license-Free-lightgrey.svg)](#-license)

**ARTE** is an advanced QGIS plugin designed for Arma Reforger terrain creators. It provides a streamlined workflow to extract high-resolution satellite imagery, process digital elevation models (DEM), apply OSM-based **Terrain Engineering**, and **automatically generate Enfusion-ready import parameters**.

<img width="751" height="768" alt="arte" src="https://github.com/user-attachments/assets/d270fdb4-6b5d-4630-a473-c4f5f08c0f96" />

## ✨ Key Features
* **Interactive Map Selection:** Visually draw, move, and resize your terrain boundaries directly on the QGIS map canvas with aspect-ratio locking.
* **Multiple Elevation Sources:**
    * **AWS Terrarium:** 30m global resolution database, **no API key required**.
    * **Mapbox Terrain-RGB:** Ideal for high-fidelity global elevation data, **requires Mapbox API key**.
    * **OpenTopography Datasets:** Gives access to premium LiDAR, COP30, AW3D30, and EU_DTM data, **requires OpenTopography API key**. *OpenTopography COP30 is highly recommended as the most optimal option.*
    * *Note: Both Mapbox and OpenTopography require a free API key to access their servers. You can easily generate your personal tokens by creating a free account on their official websites and pasting them directly into the plugin interface.*
* **OSM Terrain Engineering:** Automatically flattens heightmaps under roads/railways and smooths riverbeds using real-time OpenStreetMap data.
* **Enfusion-Ready Export:** Automatically calculates the exact `Grid cell size` and `Height scale` parameters required for the Arma Reforger Workbench.
* **Flexible Formats:** Export heightmaps as 16-bit PNG, Esri ASCII Grid (.asc), or raw Float32 GeoTIFF.

## 🛠️ OSM Terrain Engineering
When enabled, the plugin uses OpenStreetMap vector data to guide terrain modification of raw DEM data for Enfusion workflow preparation:

* **Smart OSM Filtering:** Fetches data from Overpass API (with fallback endpoints) and filters roads, rails, and water features, excluding bridges and tunnels.
* **Dynamic Road & Lane Widths:** Parses OSM tags (where available) such as width and lanes to estimate corridor widths for buffering and rasterization.
* **Pixel-Aware Embankments:** Uses buffer scaling and distance-based falloff that adapts to raster resolution (pixel size) to avoid overly sharp or blocky transitions.
* **Dual-Mask Water Processing:** Combines water line and polygon data into raster masks and applies smoothing and morphological cleanup to improve coastline continuity and reduce artifacts.
* **Riverbed Shaping:** Modifies terrain under water features using DEM-derived slope information combined with smoothing and distance falloff, applying a simplified depth offset for game-ready river profiles rather than true hydrological modeling.
* **Built-in Flood Protection:** Ensures roads and railways are not lowered below nearby water levels by applying elevation constraints during terrain modification.
* **Visual Audit Logs:** Outputs a real-time `engineer_debug_[timestamp].txt` log and a `heightmap_diff_[timestamp].tif` file showing terrain modifications for debugging and QA.

### 📊 Terrain Engineering Comparison
![Terrain Engineering Comparison](https://github.com/user-attachments/assets/93152eba-9bb0-40a6-87fb-57f6740777dd)

## 🚀 Installation
1. Download `ARTE-QGIS-plugin.zip` from [Releases](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest).
2. Open QGIS and navigate to **Plugins** -> **Manage and Install Plugins...**
3. Select the **Install from ZIP** tab, browse for the `.zip` file and click **Install Plugin**.
4. *Note: ARTE automatically registers its own update repository for seamless future updates.*

## 🛠️ Quick Usage Guide
1. Click the **ARTE icon** in the toolbar or find it under the `Arma Tools (ARTE)` menu.
2. Click **1. Load Satellite Preview** to center the map.
3. Click **2. Select Extent on Map**, drag the red bounding box, and press `ENTER` or `Right-Click` when finished.
4. Set resolutions, select your Elevation Data Source, and click **OK**.
5. Open `enfusion_import.txt` and copy the calculated scale values directly into your Arma Reforger World Editor!

---

### 📄 **License**
This project is licensed under the MIT License - free to use, modify, and distribute.

### Author 🧑‍💻
Created by **Icebird** - Copyright (c) 2026.
