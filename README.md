# Monsoon paper
All codes related to our paper "Unraveling the Mystery of Tropical Monsoon Long-Term Prediction".

---------------------------------------------------------------------------------------------------------------------------------------------------------------
In file named 'data_preprocess':
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**cal_t_ano.py**

This Python code selects specific nodes from NetCDF files containing air temperature data, reads and processes the data by cutting leap days if necessary, calculates anomalies for each year's data using different methods depending on whether the year is before or after 1952, and finally runs the anomaly calculation for all years from 1948 to 2022.

**cal_prate.py**

This Python code reads precipitation rate data from a NetCDF file, reshapes it, and calculates the mean precipitation rate for different seasons over 74 years.

**find_best_model_CFSv2_NCEP.py** / **find_best_model_SEAS5_NCEP.py** / **find_best_model_SEAS5_ERA5.py** 
These Python codes read precipitation rate data from text and NetCDF files, selects a specific region, calculates the mean precipitation rate for two seasons over multiple years and ensemble members, plots the ensemble data, and computes the Pearson correlation coefficient between the ensemble forecasts and observed data.


---------------------------------------------------------------------------------------------------------------------------------------------------------------
In file named 'networks_construction'
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**calculation.h** / **run.cpp**

This C++ code, using MPI for parallel processing, reads data of degrees and precipitation rates from text files, calculates the cross - correlation function (CCF) between them, and outputs the maximum absolute CCF values along with corresponding node indices to separate data files for different degrees and months.

**cal_degree.py**

This Python code reads network data for each year from 1949 to 2021, constructs matrices based on the data, calculates the out - degree, in - degree, and divergence degree (both sum and average) for each node in the network, and then writes the results to separate files for each year.


---------------------------------------------------------------------------------------------------------------------------------------------------------------
In file named 'predictable'
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**calculation_r1.py**

This Python code uses the multiprocessing module to parallelize the calculation of Pearson correlation coefficients between precipitation rate data and degree data. It reads the precipitation rate and degree data from text files, calculates the maximum absolute correlation coefficient for each node in the precipitation rate data against all nodes in the degree data, and saves the results to text files.

**find_predictable.py**

This Python code reads degree and precipitation rate data, merges multi-year degree data, calculates max Pearson correlation coefficients and relevant node indices, computes later-year correlation coefficients, and collects prediction info. based on correlation and significance. 


---------------------------------------------------------------------------------------------------------------------------------------------------------------
In file named 'prediction'
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**learn_test_forecast.py**

This Python code reads predictor and precipitation rate data, conducts linear regression for prediction testing and forecasting, calculates MAPE, RMSE, and Pearson correlation coefficient, normalizes the metrics, selects an optimal learning length based on a composite criterion, and plots the results. 

**prediction.py**

This Python code reads precipitation rate and predictor data, and SEAS5 or CFSv2 prediction data. It calculates prediction errors, and plots the observed and predicted precipitation rates over time, along with scatter plots comparing observed and predicted values, for different prediction models and lead times. 


---------------------------------------------------------------------------------------------------------------------------------------------------------------
In file named ' visualization'
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**draw_degree.py**

This Python code reads geographical node data and degree data for a range of years, calculates the average absolute degree, identifies significant nodes based on a percentile threshold, interpolates the data to a regular grid, and then creates a cartopy map to visualize the interpolated data with marked significant nodes and predictor locations. 

**draw_predictors.py**

This Python code reads precipitation rate data and node geographical coordinates, then uses `Basemap` to create two types of maps. The first map shows precipitation rate distribution and optionally draws great - circles between specified start and end nodes. The second map zooms in on a target region, highlights predictor nodes, and adds a rectangular area around target nodes. Finally, it runs the mapping functions with predefined target and predictor node sets for different regions. 

**draw_SEAS5_map.py** / **draw_CFSv2_map.py**

These Python codes read precipitation rate forecast data from SEAS5 and CFSv2, respectively, selects nodes within a specified geographical region, calculates the average precipitation rate for a particular season (either season 1 or season 2), and then creates a global map to visualize the precipitation rate distribution with the option to mark the selected nodes. 







