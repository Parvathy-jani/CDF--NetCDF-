# CDF--NetCDF-

# TIMED SABER Neutral Density, Temperature, and Pressure Data

This repository contains data from the TIMED SABER (Thermosphere Ionosphere Mesosphere Energetics and Dynamics) satellite mission, specifically focusing on the neutral density, neutral temperature, pressure, and other atmospheric variables as a function of latitude, longitude, and tangent point altitude.

## Data Overview

The dataset consists of multiple variables, including:

- **Neutral Density**: Atmospheric density measurements.
- **Neutral Temperature**: Kinetic temperature data.
- **Pressure**: Atmospheric pressure data.
- **Tangent Point Latitude and Longitude**: Latitude and longitude averaged at the tangent point.
- **Altitude Data**: Geopotential height and tangent point altitude.

The data is stored in a NetCDF format and includes variables across multiple dimensions, such as `Epoch`, `tpSolarLT_dim`, `tpaltitude_dim`, `pressure_dim`, `ktemp_dim`, and `density_dim`.

## Data Source

The data is sourced from the TIMED SABER L2AS dataset:

- **File Name**: `timed_l2as_saber_20211028000052_20211111235913_cdaweb.nc`
- **Path**: `C:\Users\parva\OneDrive\Desktop\Inspire_Project\Geo_B_Storm\TIMED_Pressure_Data\`

## Dimensions and Variables

The dataset contains the following dimensions:

- `Epoch`: Time dimension with 21,395 data points.
- `tpSolarLT_dim`: Solar local time dimension with 400 points.
- `tpgpaltitude_dim`: Geopotential altitude dimension with 400 points.
- `pressure_dim`: Pressure dimension with 400 points.
- `ktemp_dim`: Kinetic temperature dimension with 400 points.
- `density_dim`: Density dimension with 400 points.
- `tpaltitude_dim`: Tangent point altitude dimension with 400 points.

The key variables in the dataset include:

- `tplatitudeAVG`: Tangent point latitude averaged over the lower part of the scan.
- `tplongitudeAVG`: Tangent point longitude averaged.
- `tpSolarLT`: Tangent point local solar time.
- `tpgpaltitude`: Geopotential height at tangent point.
- `pressure`: Atmospheric pressure data.
- `ktemp`: Kinetic temperature at tangent point.
- `density`: Atmospheric neutral density.
- `tpaltitude`: Tangent point altitude.

## Data Cleaning

The dataset has been cleaned by excluding values of `-999.0`, which are used as fill values for missing or invalid data points.

```python
import xarray as xr

# Open the NetCDF file
netcdf_file = "path/to/timed_l2as_saber.nc"
ds = xr.open_dataset(netcdf_file)

# Clean the data by removing fill values (-999.0)
cleaned_data = ds.where(ds != -999.0, drop=False)

# Display cleaned data
print(cleaned_data)
