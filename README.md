# ARTE - Arma Reforger Terrain Exporter (QGIS Plugin)

[![Version](https://img.shields.io/badge/version-1.2.0-blue.svg)](https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest)
[![QGIS](https://img.shields.io/badge/QGIS-3.x-green.svg)](https://qgis.org/)
[![Engine](https://img.shields.io/badge/Engine-Enfusion%20\(Arma%20Reforger\)-orange.svg)](https://reforger.armaplatform.com/)
[![License](https://img.shields.io/badge/license-Free-lightgrey.svg)](#-license)

**ARTE** (Arma Reforger Terrain Exporter) is a modular, high-performance QGIS plugin designed for Arma Reforger terrain creators. It provides an end-to-end workflow to extract high-resolution satellite imagery, process digital elevation models (DEM), perform OSM-based **Terrain Engineering**, inspect terrain in real-time interactive 3D, and **automatically generate Enfusion-ready import parameters**.

![ARTE Interface](https://github.com/user-attachments/assets/d270fdb4-6b5d-4630-a473-c4f5f08c0f96)

---

## ✨ Key Features

* **🧩 Plug & Play Modular Architecture:** Extend functionality dynamically through isolated module scripts with custom UI hooks, export filters, and HTML report integrations.
* **🎨 Real-Time 3D & Difference Inspector:** Hardware-accelerated PyVista engine with sub-pixel terrain alignment, difference analysis, hydrological layers, and an FPS Walk Mode.
* **📐 Interactive Map Selection & Enfusion Validation:** Precision bounding box selection with 1:1 aspect-ratio locking, dynamic size tooltips in meters, and power-of-two resolution checks.
* **🌐 Flexible & Expandable Elevation Sources:**

  * **Custom Source Manager (New ✨):** Add, edit, and persist custom BBox, XYZ tile, or local DEM sources.
  * **AWS Terrarium:** 30m global dataset (**no API key required**).
  * **Mapbox Terrain-RGB:** High-fidelity terrain (**requires API key**).
  * **OpenTopography (COP30 / AW3D30 / LiDAR):** Premium datasets (**API key required**, COP30 recommended).
    *Note: Mapbox and OpenTopography require a free API key. Tokens can be generated on their official websites and added directly in the plugin UI.*
* **🛠️ Advanced OSM Terrain Engineering:** Automated road flattening, riverbed sculpting, bridge elevation constraints, NoData interpolation, and flood protection.
* **🚀 Enfusion-Ready Export:** Automatic calculation of exact `Grid cell size`, `Height scale`, and chunk grid structures for Arma Reforger Workbench.
* **📦 Flexible Formats:** Export heightmaps as 16-bit PNG, Esri ASCII Grid (`.asc`), or raw Float32 GeoTIFF.

---

## 🧩 Plug & Play Modular Architecture

ARTE features a dynamic module manager (`ArteModuleManager`) that automatically scans and initializes extension scripts (such as `01_engineer_2.py` and `03_3DView.py`) from the plugin directory.

* **Dynamic UI Injection:** Modules inject custom control panels and actions into the main plugin window without modifying core code.
* **Export Pipeline Hooks:** Intercept and manipulate raster data prior to final export.
* **Extended Reporting:** Append custom telemetry, visual audits, and metadata into the final HTML export report.

---

## 🎨 3D Terrain & Difference Inspector (`03_3DView.py`)

An interactive 3D visualization and analytical inspection environment powered by **PyVista + VTK** with Eye-Dome Lighting (EDL).

### Render Modes & Visualizations

* **Satmap Texture Mode:** Projects high-resolution satellite imagery onto 3D mesh geometry with automatic pyramids/overviews.
* **Elevation Mode:** Pure height-based visualization.
* **Wireframe Mode:** Toggleable mesh overlay.
* **Pro Difference Mode:** Elevation delta comparison between DEMs.

### Sub-Pixel Auto-Alignment & Difference Analysis

* **Automated Alignment:** Sub-pixel registration (XY + Z), including Local Flow Alignment via gradient matching and Gaussian filtering.
* **Interactive Transforms:** Rotate (`Z`), flip (`U`), transpose (`I`).
* **Real-Time Difference Filtering:** 0–100% diff slider + palette swap.

### Geomorphological & Hydrological Layers

* **Slope / Gradient**
* **Curvature**
* **Flow Accumulation**
* **3D Contours**
* **Erosion Index**

### Physics-Based FPS Walk Mode

Press `G`:

* Gravity + collision
* Jump (`Space`)
* WASD / Arrow movement
* Mouse look
* `F` teleport, `R` reset

### QGIS Integration

* Floating overlay UI + FPS stats
* Input interception (no stuck keys)
* Export diff → GeoTIFF → auto-load via `QgsRasterCalculator` (`K`)

---

## 🛠️ OSM Terrain Engineering

Uses OpenStreetMap vector data for terrain modification before export:

* **Smart OSM Filtering:** Overpass API with fallback endpoints, excluding bridges/tunnels
* **Dynamic Width Estimation:** Based on `lanes`, surface, and road class
* **Pixel-Aware Embankments:** Resolution-aware smoothing and falloff
* **Dual-Mask Water Processing:** Line + polygon merge with cleanup
* **S-Curve Riverbed Generation:** Natural shaping with constraints
* **NoData Interpolation:** `NearestNDInterpolator`
* **Flood Protection:** Prevents submerged roads/rails
* **Engineering Multiplier:** Global corridor scaling
* **Visual Audit Logs:**

  * `engineer_debug_[timestamp].txt`
  * `heightmap_diff_[timestamp].tif`

### 📊 Terrain Engineering Comparison

![Terrain Engineering Comparison](https://github.com/user-attachments/assets/93152eba-9bb0-40a6-87fb-57f6740777dd)

---

## 📐 Advanced Map Tool & Enfusion Validation

* **Precision Bounding Box (`ArmaAdvancedMapTool`):**

  * Resize handles
  * 1:1 aspect lock
  * Real-time metric tooltips

* **Independent Resolution Controls**

* **Power-of-Two Validator**

* **Chunk Grid Calculator**

* **Custom Source Manager (`CustomSourceBuilderDialog`):**

  * Persistent `sources.json`
  * Supports AWS / Mapbox / OpenTopography

---

## 🚀 Installation

1. **Download Release:**
   👉 https://github.com/Rendszerguru/ARTE-QGIS-plugin/releases/latest

2. **Open QGIS Plugin Manager:**
   **Plugins → Manage and Install Plugins...**

3. **Install from ZIP:**
   Select file → Install Plugin

4. *ARTE automatically registers its update repository*

---

## 🛠️ Quick Usage Guide

1. Launch via **ARTE icon** or `Arma Tools (ARTE)`
2. Click **Load Satellite Preview**
3. Click **Select Extent on Map** → adjust → `ENTER` / Right-click
4. *(Optional)* Configure sources
5. Set resolution + elevation source → **Process**
6. Use `enfusion_import.txt` values in Workbench

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## 🧑‍💻 Author

**Icebird** — Copyright © 2026

