# Thomas Fire Analysis

## About
This study aims to create a false-color image of the Thomas Fire using remote sensing data. It will highlight the fire scar and explore how coding and data visualization can support environmental monitoring.
- Analyze both the daily and 5-day average Air Quality Index (AQI)
- Explore the landscape using remote sensing techniques
- Visualize the fire scar with a false-color image

## Repository Structure
```bash
thomas-fire-analysis
├── README.md
├── .gitignore
├── blog.ipynb
├── data
│   ├── daily_aqi
│   │   ├── daily_aqi_by_county_2017.zip
│   │   └── daily_aqi_by_county_2018.zip
│   ├── landsat
│   │   └── landsat8-2018-01-26-sb-simplified.nc
│   └── thomas_fire
│       ├── thomas_fire.cpg
│       ├── thomas_fire.dbf
│       ├── thomas_fire.prj
│       ├── thomas_fire.shp
│       └── thomas_fire.shx
└── images
    ├── ax_map.jpg
    ├── ax_plot.jpg
    └── thomas_fire.jpeg
```

## Data
All of the datasets have been downloaded and saved in the data folder located in the repository. You can access the datasets within their corresponding subfolders.

The Daily AQI by County datasets can be accessed using the `pandas` library by setting the compression argument to "zip."
```bash
aqi_17 = pd.read_csv("data/daily_aqi/daily_aqi_by_county_2017.zip", compression = "zip")
aqi_18 = pd.read_csv("data/daily_aqi/daily_aqi_by_county_2018.zip", compression = "zip")
```
The Thomas Fire shapefile and the Landsat 8 raster can be accessed using the `os` library to create a reproducible file path. You can read the shapefile with `geopandas` and the raster with `rioxr`.
```bash
data_dir = os.path.join(os.getcwd(), "data")

thomas_fire = gpd.read_file(os.path.join(data_dir, "thomas_fire", "thomas_fire.shp"))
landsat = rioxr.open_rasterio(os.path.join(data_dir, "landsat", "landsat8-2018-01-26-sb-simplified.nc"))
```

## References
California Department of Forestry and Fire Protection. California Fire Perimeters (all) [Dataset]. Data.gov. https://catalog.data.gov/dataset/california-fire-perimeters-all-b3436

Earth Resources Observation and Science (EROS) Center. (2020). Landsat 8-9 Operational Land Imager / Thermal Infrared Sensor Level-2, Collection 2 [Dataset]. U.S. Geological Survey. https://doi.org/10.5066/P9OGBGM6

United States Environmental Protection Agency. (2024). Daily AQI by County [Dataset]. EPA. https://aqs.epa.gov/aqsweb/airdata/download_files.html#AQI

## Acknowledgements
This repository was created for a final project related to the course EDS 220: Working with Environmental Datasets.

This course is an academic requirement for the Master of Environmental Data Science (MEDS) program at the Bren School of Environmental Science & Management, University of California, Santa Barbara.