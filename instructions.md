# Instructions

## follow the following instructions

1. [ ] run the example starting code and familiarize yourself with some geosaptial processing techniques, including:
   - sampling
   - spatial join
   - geo-visualization
2. [ ] start by performing Exploratory Data Analytics (EDA) for the data > for example - historgrams to study the distribution of data (you have three sensors) - `Kernel Density (univariate, aspatial)` - get insights from the following: - [02_geovisualization](https://darribas.org/gds_scipy16/ipynb_md/02_geovisualization.html) - [Exploratory Spatial Data Analysis (ESDA)](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html) - [NYC Data](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter02/NYC%20Data.ipynb) - [Performing Spatial operations like a Pro](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter03/Chapter3.ipynb) such as `Spatial join`
   > also,
   >
   > - Exploratory Spatial Data Analysis (ESDA) [example](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html), such as `Spatial Autocorrelation`
   > - Exploratory Spatial and Temporal Data Analysis (ESTDA), [example](https://darribas.org/gds_scipy16/ipynb_md/05_spatial_dynamics.html), such as `Spaghetti Plot`, `Kernel Density (univariate, aspatial)`, `Markov Chains`, and `Spatial Markov`, [Spatial Autocorellation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb), and [GLobal Spatial Autocorrelation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb)
3. [ ] Find the example notebook titled `shortest-path.ipynb`.
   > You need to find the street network of NYC and join (`spatial join`) the sensor's reading you have in the .csv file (air quality sensor's readings collected from NYC), then you will have a new file containing the readings and to which street (edge in OSMNX terms) they belong each, then you can compute, for example, the average PM10 value in each street segment, then this would be the `weight` that you can pass to the `shortest_path` function in `osmnx`. This is not binding!!!, depending on your `EDA` and `ESDA` and `ESTDA`, you decide what is the `weight` that you want to pass to the `shortest_path` function in `osmnx`.
4. Then, given an origin point and a destination, > what is the `shortest path` that minimizes the total `PM10` exposure. Imagine a scenario where a lady dweller is walking a baby on a trolley and she is trying to avoid the areas that are most polluted by navigating your map that recommends shortest path in terms of less pollution (less exposure to PM10, in total!) -
   **_Team members_**

- [[Eisa Sajwani]()](https://github.com/EisaSajwani)
- [[Eisa Ali Alsaadi]()](https://github.com/eisaaliedu)
- [Dr. Isam Al Jawarneh](https://isamaljawarneh.github.io/)
