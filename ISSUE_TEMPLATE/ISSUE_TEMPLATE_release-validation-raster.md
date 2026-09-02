---
name: Pre-release validation (raster)
about: Check if the data product is valid
title: "DATA-PRODUCT_vX.X_release-validation-raster"
labels: Data
type: task
assignees: ''
---

**Raster data**

This checklist is developed for raster geospatial data (usually, GeoTIFF). 

1. [ ] 🛡️ **Integrity**
    - [ ] *file opens* in desktop GIS (eg, QGIS)
    - [ ] *file renders* correctly at different scales in desktop GIS for the whole area of interest without artefacts 
        > Note: Rendering artefacts (eg, missing blocks when zooming in/out) might signal file errors.
    - [ ] *file size* reasonable for sharing
        > Note: for the current Data Catalogue, it's recommended to keep size under 150 MiB
    - [ ] dataset uploaded to the Data Catalogue can be *downloaded with the correct file extension*
        > Example: `your_data.tif`, not `your_data`

2. [ ] 📊 **Statistics**
    - [ ] *number of null values* aligns with our intention 
        > Default: 0
    - [ ] *value range* (min/max) is valid
        > Example: For probabilities (eg, cloud probability) you expect (0...1)

3. [ ] 🗂️ **Metadata**
    - [ ] metadata is created based on the [project JSON template](https://github.com/Imago-SDRUK/Imago-RSE-Team/blob/main/templates/data_product_metadata_template.json)
        > [Example of filled metadata](https://github.com/Imago-SDRUK/Imago-RSE-Team/blob/main/templates/data_product_metadata_template.json)
    - [ ] correct *CRS* encoded 
        > Default: CRS:27700
    - [ ] *extent and spatial resolution* align with intention
        > Default: UK National Grid tile of 20km * 20km
    - [ ] correct *compression* algorithm 
        > Example: LZW or None
    - [ ] *layout*, if required
        > Default: no
    - [ ] *no-data value* encoded (if required)
    - [ ] *band names* are correct (if required)
    - [ ] all used datasets are referenced in the dataset tracker
        > [Dataset list](https://theuniversityofliverpool.sharepoint.com/:x:/r/sites/imago-O365-Team/Shared%20Documents/01.%20Imago%20delivery%20(General)/09.%20Imago%20Data/Datasets_Tracker.xlsx?d=w983a1df8338e47288188b3e38d476caf&csf=1&web=1&e=3Nd4m6)
    - [ ] short descriptions of all bands are provided as human-readable text
        > Example: *band1_tmp* - Annual average temperature

5. [ ] ☁️ **Storage** - Azure Cloud
    - [ ] raw/intermediate datasets are uploaded into the relevant container
    - [ ] output datasets are uploaded into the relevant container
        > Example: output CLiVE temperature data product v1.0.0 → `CLiVE/temperature_1.0.0/output/`