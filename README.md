# ARTE - Arma Reforger Terrain Exporter (QGIS Plugin)

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest)
[![QGIS](https://img.shields.io/badge/QGIS-3.x-green.svg)](https://qgis.org/)
[![Engine](https://img.shields.io/badge/Engine-Enfusion%20(Arma%20Reforger)-orange.svg)](https://reforger.armaplatform.com/)
[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](#)

**ARTE** is an advanced QGIS plugin designed specifically for Arma Reforger terrain creators. It provides a seamless workflow to extract high-resolution Google Satellite imagery, fetch digital elevation models (DEM), apply terrain engineering, and automatically generate the necessary import parameters for the Enfusion Engine.

## ✨ Key Features

* **Interactive Map Selection:** Visually draw, move, and resize your terrain boundaries directly on the QGIS map canvas with aspect-ratio locking.
* **Multiple Elevation Sources:**
  * **AWS Terrarium:** Free, global 30m coverage.
  * **Mapbox Terrain-RGB:** High detail (API Key required).
  * **OpenTopography:** Direct access to LiDAR and high-res datasets like COP30, AW3D30, and EU_DTM (API Key required).
* **OSM Terrain Engineering:** Automatically flattens the heightmap under roads/railways and smooths riverbeds using real-time OpenStreetMap data.
* **Enfusion-Ready Export:** Automatically calculates the exact `Grid cell size` and `Height scale` parameters required for the Arma Reforger Workbench.
* **Flexible Formats:** Export heightmaps as 16-bit PNG (Recommended for Enfusion), Esri ASCII Grid (.asc), or raw Float32 GeoTIFF.

## 🚀 Installation

1. Download the latest `ARTE-QGIS-plugin.zip` from the [Releases](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest) tab.
2. Open QGIS and navigate to **Plugins** -> **Manage and Install Plugins...**
3. Select the **Install from ZIP** tab.
4. Browse for the downloaded `.zip` file and click **Install Plugin**.
5. *Note: ARTE automatically registers its own update repository, meaning all future updates will appear seamlessly in your QGIS Plugin Manager!*

## 🛠️ Quick Usage Guide

1. Click the **ARTE icon** in the QGIS raster toolbar (or find it under the `Arma Tools (ARTE)` menu).
2. Click **1. Load Satellite Preview** to center the map on your desired coordinates.
3. Click **2. Select Extent on Map**. A red bounding box will appear. Drag the corners to resize or move it. Press `ENTER` or `Right-Click` when finished.
4. Adjust your desired Heightmap and Satellite image resolutions (e.g., 4096x4096px).
5. Select your Elevation Data Source.
6. Click **OK**.
7. Once finished, open the generated `enfusion_import.txt` file and copy the calculated scale values directly into your Arma Reforger World Editor!
