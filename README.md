# Weather-Analysis


NOTE: Statistical Observations made based on WeatherPy analysis are located at the top of the WeatherPy.ipynb notebook.


Part I: WeatherPy

This functionality generates random latitude and longitude values to be used to perform analysis on weather conditions relative to proximity to the equator.

WeatherPy uses a uniform random number generator to generate lists of floating point numbers we will use to pull nearest city names from citipy.  Using the resultant list of
city names, we make calls to the OpenWeatherMap API, printing a log to the console and to a log file for each call, collecting weather data to build a weather dataframe.  Any
rows with invalid data (humidity > 100%) are dropped.  A CSV file will be created in the output_data directory to store the dataframe for later use.

Once we have created the dataframe, we use the data to create scatter plots depicting:

    Temperature (F) vs. Latitude
    Humidity (%) vs. Latitude
    Cloudiness (%) vs. Latitude
    Wind Speed (mph) vs. Latitude

![image](/output_data/LatvHumidity_scatter01-07-2021.png)

We then perform linear regression on and plot the following relationships:

    Northern Hemisphere - Temperature (F) vs. Latitude
    Southern Hemisphere - Temperature (F) vs. Latitude
    Northern Hemisphere - Humidity (%) vs. Latitude
    Southern Hemisphere - Humidity (%) vs. Latitude
    Northern Hemisphere - Cloudiness (%) vs. Latitude
    Southern Hemisphere - Cloudiness (%) vs. Latitude
    Northern Hemisphere - Wind Speed (mph) vs. Latitude
    Southern Hemisphere - Wind Speed (mph) vs. Latitude
    
    
 ![image](/output_data/Northern_LatvHumidity_linregress01-07-2021.png)

A PNG image is saved in the output_data directory for each scatter plot.


Part II - VacationPy


VacationPy reads in the weather data CSV file from Part I, and creates a heatmap plotting latitude and longitude, and is weighted on humidity.

We then narrow down the dataset using the following criteria:
    Maximum temperature >= 70 degrees F and <= 85 degrees F
    Average humidity < 60%
    Average wind speed < 10 mph
    Average cloudiness < 70%



For each resultant city in the narrowed dataset, we search the Google Places API to find the first hotel located within 5000 meters of the coordinates.
Any rows where there is no hotel within 5000 meters of the city are dropped.


The hotels are plotted on top of the humidity heatmap with each pin containing the Hotel Name, City, and Country.

![image](/output_data/VacationPy_heatmap.png)


Outputs:
City/Weather CSV file (output_data/cities.csv)
Log file (output_data/log_file.txt)
PNG files for each scatter plot and linear regression (in output_data)
A screenshot of the heatmap with hotel pins (output_data/VacationPy_heatmap.png)
Observations made on the WeatherPy data scatterplots, located at the top of the WeatherPy jupyter notebook
Short description after each scatterplot


