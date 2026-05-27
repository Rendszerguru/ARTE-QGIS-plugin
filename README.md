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

## 🛠️ Deep Dive: OSM Terrain Engineering
When enabled, the plugin automatically sculpts raw DEM data using live OpenStreetMap vectors to ensure the landscape is instantly ready for the Enfusion engine:

* **Overpass Server Fallback:** Fetches live road, rail, and water data from OpenStreetMap, automatically switching between 3 fallback servers for zero downtime.
* **Infrastructure Filtering:** Isolates main highways, secondary roads, tracks, railways, and rivers, while intelligently bypassing bridges and tunnels to prevent terrain clipping.
* **Dynamic Width Buffers:** Generates exact vector masks scaled to your target pixel size (e.g., Heavy Roads: 12m, Rails: 8m, Medium Roads: 6.5m).
* **Cross-Flat Smoothing:** Uses Euclidean Distance Transforms (EDT) and multi-pass Gaussian Blurs to create perfectly flat, realistic embankments under infrastructure, avoiding sharp, stepped artifacts.
* **Waterway Carving:** Smooths riverbeds to the local terrain slope and carves a natural gradient depression (-0.7m) with soft falloff margins.
* **Visual Audit Logs:** Outputs a real-time `engineer_debug_[timestamp].txt` log and a `heightmap_diff_[timestamp].tif` difference map so you can visually audit every terrain modification.

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
