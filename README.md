# Overview
This project predicts PM2.5 levels for St. Eriksgatan 83, Stockholm, Sweden, using historical weather data and the previous three days of PM2.5 measurements. 

# Scripts
- 1_air_quality_feature_backfill.ipynb gathers historical weather data and PM2.5 values, performs data collection and cleaning. The processed data is stored in Feature Groups within the Hopsworks platform.

- 2_air_quality_feature_pipeline.ipynb on a daily basis retrieves the current PM2.5 value and augments it with lagged values from prior days. It also collects weather forecasts and integrates both sets of data into Hopsworks Feature Groups, ensuring that the system has an updated dataset for predictions.

- 3_air_quality_training_pipeline.ipynb combines selected features into a Feature View in Hopsworks, preparing the dataset for training. It trains an XGBoost regression model using the data, tests model performance, and saves the trained model to Hopsworks model registry.

- 4_air_quality_batch_inference.ipynb performs batch inference on a daily basis. It predicts PM2.5 values using weather forecast data and historical PM2.5 trends. Predictions are saved back into a Hopsworks Feature Group.

# Links
[Project Dashboard](https://maxdougly.github.io/mlfs-book/air-quality/)
[Air Quality Data](https://api.waqi.info/feed/@10523)
[Weather Data](https://open-meteo.com/en/docs/historical-weather-api#hourly=&daily=temperature_2m_mean,precipitation_sum,wind_speed_10m_max,wind_direction_10m_dominant)

