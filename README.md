# Mediterranean Sea Temperature & Salinity Analysis: ERA5 vs. SSP245

Comparison of historical reanalysis data (ERA5, 2011–2021) against a moderate-emissions
climate projection (SSP245, CMIP6, 2079–2089) at a Mediterranean Sea grid point, looking
at sea temperature and salinity: their seasonal cycles, long-term trends, and how the
two variables relate to each other.

## Key Results

- **Temperature:** SSP245 projects the mean annual cycle to be **2.6–4.3 °C warmer**
  than the ERA5 baseline in every month, with the largest increase in April–June and
  the smallest in winter.
- **Salinity:** the projected change is **not uniform across the year** — winter
  months show a slight *decrease* (down to −0.10 PSU) while summer months show an
  *increase* (up to +0.33 PSU), meaning the seasonal salinity cycle amplifies rather
  than shifts in one direction.
- **Temperature–salinity coupling:** the anomaly correlation is weak historically
  (r = 0.122) but strengthens noticeably in the projected period (r = 0.386),
  suggesting the two variables become more tightly coupled under future warming.

Full statistics (mean, standard deviation, min, max, annual trend) for both variables
and both periods are in [`outputs/statistics_table.xlsx`](outputs/statistics_table.xlsx).

## Method

1. Load and inspect the raw monthly ERA5 and SSP245 time series.
2. Compute descriptive statistics and monthly climatologies (mean annual cycle).
3. Compare historical vs. projected climatologies and seasonal (winter/summer) means.
4. Remove the climatology to isolate monthly anomalies, and fit a linear trend to each.
5. Summarize results in an exportable table.
6. Examine the temperature–salinity anomaly correlation in both periods.

## Tech Stack

- `xarray` — loading and manipulating labeled multi-dimensional NetCDF data
- `pandas` — building the summary results table, Excel export
- `numpy` — linear trend fitting
- `matplotlib` — all plots

## Data

The three NetCDF files used in this analysis (`era5_temp.nc`, `era5_sal.nc`,
`ssp245_temp_sal.nc`) are included in the [`notebook/`](notebook/) folder, alongside
the notebook itself. The notebook opens them by relative path (e.g. `era5_temp.nc`), so they need
to stay in the same folder as the `.ipynb` file. Clone the repo and run as-is.

## Running It

```bash
pip install -r requirements.txt
```

Then run
[`notebook/mediterranean_temperature_salinity_analysis.ipynb`](notebook/mediterranean_temperature_salinity_analysis.ipynb)
top to bottom.
