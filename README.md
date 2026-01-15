# 🥒 The Pickleball Arbitrage: Gentrification Alpha Scanner

> **"Pickleball isn't just a sport. It is a localized demand shock."**

## 📊 Executive Summary
This repository contains the Python logic used to identify **"Local Monopolies"** within the Malaysian F&B market. 

By layering **OpenStreetMap (OSM)** geospatial data over specific high-yield target zones (Pickleball Courts), this script calculates a **"Gentrification Score"** for every court in the country. The goal is to identify locations with **High Demand (Verified Traffic)** but **Zero Supply (No Mamaks)** within a 500m walking radius.

**Target Audience:** F&B Investors, Site Scouts, Commercial Real Estate Analysts.

---

## 🧠 The Methodology

### 1. Variable A: "Digital Gravity" (Demand Proxy)
Without access to proprietary credit card data, we verify footfall using **OSM Node Density**.
* **Logic:** A court that is explicitly tagged `sport=pickleball` or `name~"Pickleball"` in the OpenStreetMap database indicates a high level of community engagement and digital verification. 
* **The Filter:** We reject generic `leisure=pitch` nodes to avoid "Ghost Towns" (abandoned badminton courts). Only verified, active Pickleball hubs pass the first filter.

### 2. Variable B: The "Grease Index" (Supply Saturation)
This measures the density of existing competition within the "Momentum Radius" (500m).
* **The Radius:** 500 meters is the maximum distance a group of sweaty players will walk before the friction of "cooling down" forces them to drive home.
* **The Detection:** The script scans for specific competitors using a `Grease Keyword` dictionary (`mamak`, `nasi kandar`, `bistro`, `restoran`) and OSM keys (`amenity=restaurant`, `cuisine=mamak`).
* **The Penalty:** Each confirmed competitor acts as a "Supply Penalty," reducing the location's score.

---

## 🧮 The "Alpha" Algorithm

The script calculates a proprietary **Dead Zone Alpha Score (0-100)** for every location.

$$Score = (Base \ Prudence \ Cap) - (Commercial \ Noise \ \times \ 2)$$

* **Base Prudence Cap (98):** We never award a score of 100. In data science, a perfect score implies perfect information, which does not exist in real estate. We apply a **-2% Uncertainty Buffer** to every asset.
* **Commercial Noise:** The count of verified competitors within the radius.
* **The Threshold (85):**
    * **Score > 85 (The Arbitrage Zone):** "Local Monopoly." High traffic, zero friction. Immediate Buy.
    * **Score < 85 (Red Ocean):** "Saturated." The search cost for food is zero. Margins will be destroyed by competition.

---

## 🛠️ Usage

### Prerequisites
* Python 3.x
* `overpy` (Overpass API wrapper)
* `pandas` (Data manipulation)
* `matplotlib` & `seaborn` (Visualization)

### Quick Start
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/YourUsername/Pickleball-Gentrification-Alpha.git](https://github.com/YourUsername/Pickleball-Gentrification-Alpha.git)
    ```
2.  **Install Dependencies:**
    ```bash
    pip install overpy pandas matplotlib seaborn
    ```
3.  **Run the Scanner:**
    ```bash
    python pickleball_scanner.py
    ```

---

## ⚠️ Disclaimer
*This tool provides geospatial analysis based on public OpenStreetMap data. It does not constitute financial advice. Physical site verification is mandatory before deploying capital. The author assumes no responsibility for F&B ventures that fail due to bad cooking, even if the location score was 98.*

---

**Author:** Muhammad Ikhwan Afif  
*Finance & Economics | Quant-Hybrid*
