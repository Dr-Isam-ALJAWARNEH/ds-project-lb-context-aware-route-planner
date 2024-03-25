# Instructions
## follow the following instructions
1. [ ] run the example starting code and familiarize yourself with some geosaptial processing techniques, including:
    - sampling
    - spatial join
    - geo-visualization
3. [ ] start by performing Exploratory Data Analytics (EDA) for the data
    > for example
        - historgrams to study the distribution of data (you have three sensors)
        - ```Kernel Density (univariate, aspatial)```
        - get insights from the following:
    - [02_geovisualization](https://darribas.org/gds_scipy16/ipynb_md/02_geovisualization.html)
    - [Exploratory Spatial Data Analysis (ESDA)](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html)
    - [NYC Data](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter02/NYC%20Data.ipynb)
    - [Performing Spatial operations like a Pro](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter03/Chapter3.ipynb) such as ```Spatial join```
> also,
> - Exploratory Spatial Data Analysis (ESDA) [example](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html), such as ```Spatial Autocorrelation```
> - Exploratory Spatial and Temporal Data Analysis (ESTDA), [example](https://darribas.org/gds_scipy16/ipynb_md/05_spatial_dynamics.html), such as ```Spaghetti Plot```, ```Kernel Density (univariate, aspatial)```, ```Markov Chains```, and ```Spatial Markov```, [Spatial Autocorellation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb), and [GLobal Spatial Autocorrelation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb)
4. [ ] Find the example notebook titled ```shortest-path.ipynb```. 
    > You need to find the street network of NYC and join (```spatial join```) the sensor's reading you have in the .csv file (air quality sensor's readings collected from NYC), then you will have a new file containing the readings and to which street (edge in OSMNX terms) they belong each, then you can compute, for example, the average PM10 value in each street segment, then this would be the ```weight``` that you can pass to the ```shortest_path``` function in ```osmnx```. This is not binding!!!, depending on your ```EDA``` and ```ESDA``` and ```ESTDA```, you decide what is the ```weight``` that you want to pass to the ```shortest_path``` function in ```osmnx```. 
5. Then, given an origin point and a destination, 
    > what is the ```shortest path``` that minimizes the total ```PM10``` exposure. Imagine a scenario where a lady dweller is walking a baby on a trolley and she is trying to avoid the areas that are most polluted by navigating your map that recommends shortest path in terms of less pollution (less exposure to PM10, in total!)
------------------------

NEW! 25 March 2024

- You next task, is to extract street segments in NYC in the form of geojson (use the attached examples as a jumping off point), geojson file  will contain geometry columns consisting of a linestring for each street segment. 
- For each point in the AQ data csv file, find the corresponding street segments which is the nearest. You need to use [GeoDataFrame.sjoin_nearest](https://geopandas.org/en/stable/docs/user_guide/mergingdata.html). Explore it in details [sjoin_nearest](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.sjoin_nearest.html#geopandas.GeoDataFrame.sjoin_nearest). By this we know to which street each point (AQ reading) belongs. 
- Find the shortest path based on the pm25 as the weight. in the ```shortest_path(G,                         orig_node,    dest_node,        weight='length')``` change the weight to ```pm```. Change the ```method``` parameter to ```bellman-ford``` and compare the results, combination of two algorithms (distance + pollution level) compare ```bellman-ford``` and ```dijkstra``` in terms of Kilometer distance, remeber both of them give us optimized shortest path in terms of ```pm``` compare which one is guranteed less kilometers (a combination).
- Make a page similar to the following [green path](https://green-paths.web.app/) using [leaflet](https://leafletjs.com/)
- BONUS point: use a a ```linear weighting method```  to construct a new weight that is based on both distance and pm, and recommend route based on that!