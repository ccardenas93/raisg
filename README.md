# LULC_analysis.ipynb Overview

This notebook analyzes Land Use and Land Cover (LULC) changes in Ecuadorian river basins between 2004 and 2023 using raster and vector geospatial data. It processes, masks, and summarizes classified land cover rasters, comparing historical and recent data, and generates both tabular and visual outputs.

## Main Steps and Functionality

### 1. **Library Installation and Import**
- Installs and imports geospatial and data science libraries (`rasterstats`, `rasterio`, `geopandas`, `pandas`, `matplotlib`, etc.).

### 2. **Legend Definition**
- Defines a dictionary mapping LULC raster class codes to descriptive names (in Spanish), to translate raster values into meaningful categories.

### 3. **Data Loading and Preparation**
- Loads a **basins vector file** (`hybas6_7ECclip.gpkg`) with the boundaries of river basins.
- Loads **land cover rasters** for two years (2004 and 2023).
- Ensures both vector and raster data use the same coordinate reference system (CRS).

### 4. **Raster Masking**
- Clips (masks) both the 2004 and 2023 land cover rasters to the extent of the river basins.
- Output: New raster files limited to the study area.

### 5. **Zonal Statistics**
- Computes the count of each land cover class **per basin** for both years using `zonal_stats` (categorical mode).
- Calculates the percentage area of each class per basin for each year.

### 6. **Result Compilation**
- Compiles results into a table:
  - Basin ID
  - Land cover class (code and name)
  - Percentage of each class in each basin for 2004 and 2023
- Outputs this summary as a CSV file (`landcover_percentage.csv`).

### 7. **Change Analysis and Visualization**
- Loads the CSV and computes the change in percentage cover for each class in each basin.
- Identifies the land cover class with the largest net change across all basins.
- Plots:
  - A horizontal bar chart showing overall change per land cover class.
  - Individual bar charts for land cover change by class **for each basin**.

---

## Key Inputs

- **Vector Basins File**: `hybas6_7ECclip.gpkg` (river basin polygons)
- **Land Cover Rasters**:
  - `mapbiomas-ecuador-collection-20-2023.tif` (2023)
  - `ecuador_coverage_2005.tif` (2004)

## Key Outputs

- **CSV Table**: `landcover_percentage.csv` — summary of LULC percentages per basin for both years.
- **Plots**: Visualizations of changes in land cover both overall and per basin.

## Typical Use Case

This notebook is useful for environmental scientists, geographers, or policy makers interested in:
- Quantifying land cover change over time (e.g., deforestation, urbanization, agriculture expansion) at the river basin level.
- Identifying which land cover types are most dynamic.
- Generating publication-ready plots and summary tables for reports or further spatial analysis.

## Requirements

- Python 3.x with the following packages: `geopandas`, `rasterio`, `rasterstats`, `pandas`, `matplotlib`, etc.
- Local access to the input rasters and vector file.

---

## Notes

- Paths are hardcoded for local use (Windows format); adjust file paths as needed.
- The notebook uses Spanish class names and some file names; adapt as needed for different study areas or languages.
- The analysis focuses on percentage change, not absolute area (unless modified).
