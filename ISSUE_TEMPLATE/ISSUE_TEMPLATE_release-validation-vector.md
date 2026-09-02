---
name: Pre-release validation (vector)
about: Check if the data product is valid
title: "DATA-PRODUCT_vX.X_release-validation-vector"
labels: Data
type: task
assignees: ''
---

**Vector data**

This checklist is developed for vector geospatial data (mostly GeoPackages). Some of the checks below can also be performed on tabular (CSV) data, where applicable.

1. [ ] 🛡️ **Integrity**
    - [ ] *file opens* in desktop GIS (eg, QGIS)
    - [ ] *file renders* correctly at different scales in desktop GIS
        > Note: Rendering artefacts (eg, missing geometries when zooming in/out) might signal geometry errors.
    - [ ] *empty values* do not persist in columns (by default)
    - [ ] *file size* reasonable for sharing
        > Note: for the current Data Catalogue, it's recommended to keep size under 150 MiB
    - [ ] dataset uploaded to the Data Catalogue can be *downloaded with the correct file extension*
        > Example: `your_data.gpkg`, not `your_data`


2. [ ] 🌍 **Geography/geometry**
    - [ ] *geometry type* follows intention 
        > Example: Polygon or MultiPolygon for LSOAs.
    - [ ] *duplicates* do not persist (either by unique ID, or by geometry)
    - [ ] *empty geometries* do not persist
    - [ ] *topology validity*
        > Example: self-intersection or duplicated nodes, such as [here](https://docs.qgis.org/3.40/en/docs/user_manual/plugins/core_plugins/plugins_geometry_checker.html)

3. [ ] 📊 **Statistics**
    - [ ] *feature count* follows the intention
        > Example: should match the number of LSOAs
    - [ ] *value range* (min/max) is valid
        > Example: LSOA-aggregated value range is smaller than the input raster value range

4. [ ] 🗂️ **Metadata**
    - [ ] metadata is created based on the [project JSON template](https://github.com/Imago-SDRUK/Imago-RSE-Team/blob/main/templates/data_product_metadata_template.json)
        > [Example of filled metadata](https://github.com/Imago-SDRUK/Imago-RSE-Team/blob/main/examples/data_product_metadata_example.json)
    - [ ] correct *CRS* encoded 
        > Default: CRS:27700
    - [ ] *column names* follow the intention 
        > Example: you wanted `bandA00`, but somehow it became `band1` column in your workflow
    - [ ] *data types* follow the intention
        > Example: float could have been non-intentionally converted into integer during processing
    - [ ] *layer name* is meaningful (for GPKG)
    - [ ] all used datasets are referenced in the dataset tracker
        > Internal: [dataset list](https://theuniversityofliverpool.sharepoint.com/:x:/r/sites/imago-O365-Team/Shared%20Documents/01.%20Imago%20delivery%20(General)/09.%20Imago%20Data/Datasets_Tracker.xlsx?d=w983a1df8338e47288188b3e38d476caf&csf=1&web=1&e=3Nd4m6)
    - [ ] short descriptions of all fields (columns) are provided as human-readable text or metadata (JSON)
        > Example: *area* - Total feature area in square kilometers

5. [ ] ☁️ **Storage** - Azure Cloud
    - [ ] raw/intermediate datasets are uploaded into the relevant container
    - [ ] output datasets are uploaded into the relevant container
        > Example: output CLiVE temperature data product v1.0.0 → `CLiVE/temperature_1.0.0/output/`