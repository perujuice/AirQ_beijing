# Overview

<a href="https://www.kaggle.com/datasets/sid321axn/beijing-multisite-airquality-data-set/data"> Data </a>


**Problem:** Predict next-hour (t+1) PM2.5 at a single monitoring station within one city (Beijing).


# Description of Data

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Description</th>
      <th>Type / Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>No</td><td>Row number</td><td>DROPPED</td></tr>
    <tr><td>year</td><td>Year of data</td><td>Ordinal (integer)</td></tr>
    <tr><td>month</td><td>Month of data</td><td>Ordinal (1–12); can use cyclic encoding</td></tr>
    <tr><td>day</td><td>Day of data</td><td>Ordinal (1–31); optional cyclic encoding</td></tr>
    <tr><td>hour</td><td>Hour of data</td><td>Ordinal (0–23); optional cyclic encoding</td></tr>
    <tr><td>PM2.5</td><td>PM2.5 concentration (µg/m³)</td><td>Continuous</td></tr>
    <tr><td>PM10</td><td>PM10 concentration (µg/m³)</td><td>Continuous (DROPPED)</td></tr>
    <tr><td>SO2</td><td>SO2 (Sulfur dioxide) concentration (µg/m³)</td><td>Continuous</td></tr>
    <tr><td>NO2</td><td>NO2 (nitrogen dioxide) concentration (µg/m³)</td><td>Continuous</td></tr>
    <tr><td>CO</td><td>CO (carbon monoxide) concentration (µg/m³)</td><td>Continuous</td></tr>
    <tr><td>O3</td><td>Ozone concentration (µg/m³)</td><td>Continuous</td></tr>
    <tr><td>TEMP</td><td>Temperature (°C)</td><td>Continuous</td></tr>
    <tr><td>PRES</td><td>Pressure (hPa)</td><td>Continuous</td></tr>
    <tr><td>DEWP</td><td>Dew point temperature (°C)</td><td>Continuous</td></tr>
    <tr><td>RAIN</td><td>Precipitation (mm)</td><td>Continuous</td></tr>
    <tr><td>wd</td><td>Wind direction</td><td>Nominal categorical (one-hot or label encode)</td></tr>
    <tr><td>WSPM</td><td>Wind speed (m/s)</td><td>Continuous</td></tr>
    <tr><td>station</td><td>Name of air-quality monitoring site</td><td>Nominal categorical (one-hot or label encode)</td></tr>
  </tbody>
</table>



# Exploratory analysis: key decisions

## Missing values:
- There are not so many missing values proportionally, with no column exceeding a proportional missingness of 4%, most below 1%.  

The PM2.5 row is the target variable, since we have a lot of data, we drop the rows with the target variable missing.

# Scaling, normalization and/or standardisation

# Train/Test splot
- We should make sure not to stratify when splitting to maintain the datetime order

# k fold cross validation - grid search (hyperparameter tuning)



