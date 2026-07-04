# lahore-parks-accessibility-analysis
"Geospatial analysis of park accessibility and equity across Lahore District using Python, GeoPandas, and OSMnx"
# Lahore Parks Accessibility & Equity Analysis

A fully reproducible geospatial analysis of public park distribution, walkability, and per-capita equity across the seven tehsils of Lahore District, Pakistan — built entirely in Python using OpenStreetMap data, official 2023 census population figures, and administrative boundary shapefiles.

## Key Findings

- **77%** of Lahore District lies more than a 10-minute walk from any qualifying park
- **880** verified parks identified via OpenStreetMap across the district
- Park access varies by nearly **8x** between the best- and worst-served tehsils
- **Lahore District** (the historic urban core) is the most park-rich tehsil; **Shalimar**, a large peripheral tehsil, is the least

## Contents

| File | Description |
|---|---|
| `Lahore_Parks_Accessibility_Analysis.ipynb` | Full Python analysis notebook — data loading, cleaning, spatial analysis, and map generation |
| `Lahore_Parks_Accessibility_Report.docx` | Full written report with detailed methodology, code, and findings |
| `01_Parks_Distribution_Lahore_v2.png` | Map of all 880 parks across the district |
| `02_Walkability_Analysis_v2.png` | 10-min / 15-min walkability coverage and park desert map |
| `03_Parks_Per_Capita_by_District.png` | Choropleth of parks per 1,000 residents by tehsil |
| `04_Parks_Per_Capita_Bar_Chart.png` | Ranked bar chart comparing all seven tehsils |
| `interactive_parks_map.html` | Interactive Folium web map — download and open in any browser |
| `parks_per_district_summary.csv` / `.xlsx` | Final summary statistics table |

## Methodology Summary

1. Loaded tehsil boundaries and 2023 census population data, verified name-matching before joining
2. Reprojected all geometries to EPSG:32643 (UTM Zone 43N) for accurate distance and area calculations
3. Extracted park and amenity data from OpenStreetMap using OSMnx
4. Cleaned and filtered parks by a minimum size of 1,000 m² to remove mapping artifacts (1,058 → 880 parks)
5. Modeled 800m (10-min) and 1,200m (15-min) walkability buffers from park boundaries
6. Calculated parks-per-1,000-residents by tehsil via spatial join
7. Classified tehsils into relative equity tiers using quantile-based ranking
8. Identified "park deserts" — areas beyond a 10-minute walk from any park
9. Produced static and interactive maps for the final analysis

Full methodology, including all code, is documented in `Lahore_Parks_Accessibility_Report.docx`.

## Tools & Libraries

Python · GeoPandas · OSMnx · Shapely · Pandas · Matplotlib · Contextily · Folium · NumPy — run entirely in Google Colab.

## Data Sources

- [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors (parks, playgrounds, benches, parking)
- Pakistan Bureau of Statistics, Census 2023 (tehsil-level population)
