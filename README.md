# London Bike Share Analysis
This analysis investigates a dataset about London bike shares. Each observation is a 1-hour interval of a 2-year long period. Additionally, each observation also contains information about the number of bike shares purchased, the weather, and the season.

## Cleaning the data
I conducted some preliminary data cleaning and exploration in python to make creating visualizations in Tableau smoother. For example:

#### Renaming the columns
```python
new_cols_dict = {
    'timestamp':'time',
    'cnt':'count',
    't1':'temp_real_C',
    't2':'temp_feels_C',
    'hum':'humidity_percent',
    'wind_speed':'wind_speed_kph',
    'weather_code':'weather',
    'is_holiday':'is_holiday',
    'is_weekend':'is_weekend',
    'season':'season'}

bikes.rename(new_cols_dict, axis=1, inplace=True)
```

#### Mapping coded variables
```python
np.sort(bikes.weather.unique())
weather_dict = {
    1:'Clear',
    2:'Scattered clouds',
    3:'Broken clouds',
    4:'Cloudy',
    7:'Rain',
    10:'Rain with thunderstorm ',
    26:'Snowfall'}

bikes.season.unique()
season_dict = {
    0:'Spring',
    1:'Summer',
    2:'Autumn',
    3:'Winter'}

bikes.weather = bikes.weather.map(weather_dict)
bikes.season = bikes.season.map(season_dict)
```

The final dataset:

![Screenshot of bike.head()](https://github.com/digitoby/London-Bike-Share-Analysis/blob/main/images/data_ss.jpg)

## Dashboarding in Tableau
This is the final dashboard:

![Screenshot of dashboard](https://github.com/digitoby/London-Bike-Share-Analysis/blob/main/images/london_bike_dash.png)

The dashboard is interactive, allowing the user to select a time period on the line chart. It automatically updates to show the total number of bike shares and a heatmap. The heatmap captures temperature vs wind speeds and the corresponding bike shares for those conditions.
