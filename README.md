# Air pollution predictive modeling

**Authors:** Marteinn Hjaltason & Johan Omara  
**Course:** Artificial Intelligence for Data Science  
**Institution:** Malmö University, Dept. of Computer Science and Media Technology  
**Date:** January 2026


## Project Overview
Air pollution represents one of the most critical environmental and public health challenges of the modern era. Rapid urbanization, increased dependence on fossil-fuel-based transportation, and intensified industrial activity have resulted in widespread exposure to harmful airborne pollutants. The World Health Organization (WHO) estimates that approximately 99% of the global population breathes air that exceeds recommended air quality guidelines, contributing to millions of premature deaths each year, primarily through cardiovascular and respiratory diseases.

Fine particulate matter (PM2.5) is of particular concern because its small aerodynamic diameter enables penetration deep into the lungs and entry into the bloodstream, substantially elevating health risks. Beijing, one of the world’s largest megacities, has historically experienced severe PM2.5 pollution driven by industrial emissions, traffic-related sources, and coal-based residential heating. Previous studies indicate that PM2.5 concentrations in Beijing have frequently exceeded WHO guideline values, with especially elevated levels during winter months.

The objective of this project is to forecast PM2.5 concentrations one hour ahead using temporal (time-series) information, meteorological variables, and co-pollutant measurements. We evaluate the predictive performance of tree-based models, including Random Forest and XGBoost, and compare their results with a neural network baseline.

##  Dataset
The data used for this project is the Beijing Multi-Site Air-Quality Data Set, sourced from [Kaggle](https://www.kaggle.com/datasets/sid321axn/beijing-multisite-airquality-data-set/data).

It consists of hourly observations from 12 separate air-quality monitoring stations across Beijing (e.g., Aotizhongxin, Changping, Tiantan, Wanliu). The dataset includes:
- Air & Gaseous Pollutants: PM2.5 (target variable), PM10, SO2, NO2, CO, and O3.
- Meteorological Variables: Temperature (TEMP), pressure (PRES), dew point (DEWP), wind speed (WSPM), and wind direction (wd).
- Temporal & Spatial Identifiers: Year, month, day, hour, and station location.


## Methodology
### 1. Exploratory Data Analysis (EDA) & Preprocessing

Before modeling, a comprehensive EDA was conducted to evaluate outliers, distributions, and variable correlations. A rigorous missing-data analysis was performed to determine the underlying missingness mechanism:
- Missingness Analysis: Diagnostic approaches, including t-tests and logistic regression (via statsmodels), alongside visualizations (msno), indicated that the missing data was Not Missing Completely at Random (MAR or MNAR).
- Imputation Strategy: Interpolation was selected over Multiple Imputation by Chained Equations (MICE) for continuous variables. This provided computational efficiency while perfectly suiting the regular hourly structure of the time-series data.
    - Forward Fill was applied to categorical/directional missing values (e.g., wind direction), assuming the condition remained stable from the previous hour.
    - This streamlined approach was highly justified, as the maximum missingness for any given variable was only ~4% out of 400,000 total observations.
### 2. Feature Engineering
To optimize the dataset for machine learning—particularly for the neural network baseline—several transformations were applied:
- Cyclical Encoding for Time: Hour-of-day and day-of-year variables were transformed into sine and cosine components to accurately represent the continuous, circular nature of time. Continuous timestamp features were also retained.
- Wind Direction Transformation: Wind direction was converted into radians and subsequently split into sine and cosine components, making the circular data amenable to predictive modeling.
- Skewness Correction: A log(x+1) transformation was applied to right-skewed variables. This stabilized feature distributions and improved downstream model training.

### 3. Models
We evaluated and compared three primary machine learning approaches for short-horizon forecasting:
- **Long Short-Term Memory (LSTM)**: A neural network architecture selected as the baseline for its strong ability to capture non-linear temporal dynamics in sequential data.
- **Random Forest**: A robust tree-based ensemble method known for high predictive accuracy and lower computational cost.
- **XGBoost**: A highly efficient gradient-boosting framework utilized to model the complex, nonlinear relationships in the environmental data.

## Results
The models demonstrated that one-hour-ahead PM2.5 concentrations can be forecasted with a low Mean Absolute Error (MAE) and high explanatory power

- LSTM (Top Performer): Achieved the strongest overall performance with an R² of 0.95, proving highly effective at capturing non-linear temporal dynamics
- Random Forest: Demonstrated highly competitive results with an R² of 0.90
- XGBoost: Yielded strong predictive power with an R² of 0.86.

While the LSTM yielded the highest coefficient of determination and lowest MAE, the tree-based ensembles (Random Forest and XGBoost) remain robust, computationally efficient alternatives for modeling air pollution data. Ultimately, the high accuracy of these models provides a reliable framework for short-term public health warnings and environmental policy planning.

## References

[1] World Health Organization, “Who global air
quality guidelines.” [Online]. Available: https:
//www.who.int/publications/i/item/9789240034228

[2] C. A. Pope and D. W. Dockery, “Health effects of
fine particulate air pollution,” Journal of the Air &
Waste Management Association, vol. 69, no. 4, pp.
367–384, 2019.

[3] C. K. Chan and X. Yao, “Air pollution in mega cities
in china,” vol. 42, no. 1, pp. 1–42, 2008. [Online].
Available: https://www.sciencedirect.com/science/
article/pii/S1352231007007911

[4] S. Chen, “Beijing multi-site air quality,” UCI
Machine Learning Repository, 2017. [Online].
Available: https://doi.org/10.24432/C5RK5G


