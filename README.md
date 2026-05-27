# ARTE - Arma Reforger Terrain Exporter (QGIS Plugin)

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest)
[![QGIS](https://img.shields.io/badge/QGIS-3.x-green.svg)](https://qgis.org/)
[![Engine](https://img.shields.io/badge/Engine-Enfusion%20(Arma%20Reforger)-orange.svg)](https://reforger.armaplatform.com/)
[![License](https://img.shields.io/badge/license-Free-lightgrey.svg)](#-license)

**ARTE** is an advanced QGIS plugin designed specifically for Arma Reforger terrain creators. It provides a seamless workflow to extract high-resolution Google Satellite imagery, fetch digital elevation models (DEM), apply terrain engineering, and automatically generate the necessary import parameters for the Enfusion Engine.

<img width="751" height="768" alt="arte" src="https://github.com/user-attachments/assets/d270fdb4-6b5d-4630-a473-c4f5f08c0f96" />

## ✨ Key Features
* **Interactive Map Selection:** Visually draw, move, and resize your terrain boundaries directly on the QGIS map canvas with aspect-ratio locking.
* * **Multiple Elevation Sources:** AWS Terrarium (Free 30m), Mapbox Terrain-RGB, and OpenTopography datasets (LiDAR, COP30, AW3D30, EU_DTM). **OpenTopography COP30 is highly recommended as the most optimal option.**
* **OSM Terrain Engineering:** Automatically flattens heightmaps under roads/railways and smooths riverbeds using real-time OpenStreetMap data.
* **Enfusion-Ready Export:** Automatically calculates the exact `Grid cell size` and `Height scale` parameters required for the Arma Reforger Workbench.
* **Flexible Formats:** Export heightmaps as 16-bit PNG, Esri ASCII Grid (.asc), or raw Float32 GeoTIFF.

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
