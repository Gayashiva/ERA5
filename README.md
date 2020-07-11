# Download ERA5 and convert to ROMS format

This toolbox enables you to download ERA5 atmospheric forcing data for your model domain for a specified period.  The toolbox uses the [*Climate Data Store*] Python API to connect and download specific variables required by ROMS to perform simulations with atmospheric forcing. These variables are included in the list below:
```
   'Specific_humidity',
   '10m_u_component_of_wind',
   '10m_v_component_of_wind',
   '2m_temperature',
   '2m_dewpoint_temperature',
   'Mean_sea_level_pressure',
   'Total_cloud_cover',
   'Total_precipitation',
   'Mean_surface_net_short-wave_radiation_flux',
   'Mean_surface_net_long-wave_radiation_flux',
   'Mean_surface_downward_long-wave_radiation_flux',
   'Mean_surface_latent_heat_flux',
   'Mean_surface_sensible_heat_flux',
   'Evaporation'
```

To see the details for how ROMS requires naming convention etc. you can see more details [here].
**Install API**
To start signup and get necessary credentials at the [*Climate Data Store*]. Store the credentials in a file called `.cdsapirc`in you root `$HOME` directory. It should look something like this:

url: https://cds.climate.copernicus.eu/api/v2
key: 28122:f85a4564-8895-498d-ad8a-gf274ba38d2r

**Edit the toolbox settings**
Edit the file `ECMWF_query.py`to define the start and end period you want to download data. If you want you can edit the months, days, and time steps of the day data will be downloaded in the file `ECMWF_tools.py` but by default the program downloads data for all available reanalysis time steps of the day for all days for all months of the year. Each result file contains data for one variable for one year.

The region for where you extract the data is defined by the variable `self.area = "80/0/50/25"`found in `ECMWF_query.py`. The area is constrained by `North/West/South/East`.

**Run the toobox**
To run the toolbox after editing the settings simply run
`python ECMWF_tools.py`

**Unittest**
A few simple unittests are included in `test_ERA5.py`.
