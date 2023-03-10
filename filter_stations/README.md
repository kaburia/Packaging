## filter_stations

* Import the library and load the api Key to use it
```
from filterstations import Filter, Interactive_maps
# Retrieve the apiKey and apiSecret from a config.json file
import json 

# Authentication
with open('../bson/config.json') as f:
    conf = json.load(f)

apiKey = conf['apiKey']
apiSecret = conf['apiSecret']
```
### Usage
```
fs = Filter(apiKey, apiSecret)
```

* getStationsInfo(station=None, multipleStations=[], countrycode=None)
```
station returns the information for a particular station
multipleStations - pass in a list of the stations. return a dataframe with the particular stations
countrycode - returns a dataframe of the stations in the particular region
```
returns stations information based on the parameters passed

* filterStations(address, distance, startDate=None, endDate=None, csvfile='KEcheck3.csv')
```
address - returns a dataframe of the stations and their clog flags in that particular region
distance - the distance desired to draw a radius from a particular region
startDate & endDate - the duration desired 
csvfile - a file containing data of the stations in the format Date, station_precipitation, station_clogFlag
```
returns a dataframe of the filter

* filterStationsList(address, distance=100)
```
address - desired region
distance - radius of how far from the addres in kilometres
```
returns a list of the stations within the specified region

* k_neighbours(station, number=5)
```
station - the target station
number - number of neighbours desired
```
returns a dictionary of the stations from the closest distance in kilometres

## Interacting with the data from the maps
```
maps = Interactive_maps(apiKey, apiSecret)
```
* The maps functions are designed to work on jupyter notebooks

* draw_map(map_center)
Given the map center returns the map of the whole TAHMO stations network

* create_animation(data, valid_sensors, day=100, T=10, interval=500)
```
data - The dataframe containing the dat
valid_sensors - the columns to filter from the data
day - the rows to choose from the data
T - the range to change the animation
```
returns an animated matrix of the data

https://user-images.githubusercontent.com/88529649/224543385-3212a7c9-230a-4530-9a04-a3310e674c52.mp4

* get_map(subset1, subset2, start_date=None, end_date=None, data_values=False, csv_file='KEcheck3.csv', min_zoom=8, max_zoom=11, width=850, height=850)

```
Subset1 - a list of the stations 
subset2 - a second list of stations
```
Given two lists, this can be the valid sensors and the clogged sensors or subset1 can be a list of the entire map then subset2 the specific region chosen 
returns a map with blue being subset1 and red subset2
![image](https://user-images.githubusercontent.com/88529649/224542507-7fc9dbb7-35e6-42e4-b54b-d248dfbe7e0c.png)


To get the values of the stations for the subset on click, set the data_values to be true and choose a specific start and end date
```
width & height - the size of the popup on click
```
![image](https://user-images.githubusercontent.com/88529649/224542616-c8792564-d81e-4649-bbc2-1666f25d34ed.png)
