## follow instructions
# instructions
# `Required OPTIMIZATIONs ==> IMPORTANT!`
---------------------------------------
<!-- Task 2 -->
# Task 2
- [X] **task accomplished - Excellent!**
# `Update: April 13, 2024`
### `N.B.` references are available in the end of this instruction file!
complete tasks (or sub-tasks) marked with ```attention``` in the [Task 1](#task-1)

## `TODO:` 
- [X] start by performing more Exploratory Data Analytics (EDA) for the data > for example - historgrams to study the distribution of data (you have three sensors) - `Kernel Density (univariate, aspatial)` - get insights from the following: - [02_geovisualization](https://darribas.org/gds_scipy16/ipynb_md/02_geovisualization.html) - [Exploratory Spatial Data Analysis (ESDA)](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html) - [NYC Data](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter02/NYC%20Data.ipynb) - [Performing Spatial operations like a Pro](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter03/Chapter3.ipynb) such as `Spatial join`
   > also,
   > - Exploratory Spatial Data Analysis (ESDA) [example](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html), such as `Spatial Autocorrelation`
   > - Exploratory Spatial and Temporal Data Analysis (ESTDA), [example](https://darribas.org/gds_scipy16/ipynb_md/05_spatial_dynamics.html), some of the following, such as `Spaghetti Plot`, `Kernel Density (univariate, aspatial)`, `Markov Chains`, and `Spatial Markov`, [Spatial Autocorellation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb), and [GLobal Spatial Autocorrelation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb)
- [X]  **subtask accomplished - Excellent!** So, you have hyperlocal Air Quality data, and you need to find the shortest parth in terms of the one with the lowest cost of pollution (e.g., pm10, pm25, etc.,). So, adapting the `shortest_path` so that you use `pm25_weight` for the `weight` attribute instead of the distance attributes. The weigh is currently based only on `value` and from the data you have you need to conisder several other attributes `individually` first, then in combination using a ```linear weighting method``` similar to the description in the file attached [here](https://github.com/Dr-Isam-ALJAWARNEH/ds-project-lb-context-aware-route-planner/blob/main/literature/linear_weighting_method.pdf). Also, do the same for other attibutes. For example, `temperature` and `humidity` in the data files attached.

- [X] **sub-task accomplished - Excellent!** `ESSENTIAL FOR THE SUCCESS OF THE PROJECT!` You need to develop a amethod to perform `spatial join` between the `hyperlocal` street-level air quality data, and the `taxi mobility` data. You are specifically required to do the following task:

   - search NYC taxi cab data that temporally corresponds to the AQ data (similar time resolution)
      > be ware that the time and space (geo dimension) resolutions, take distance (time & space) tolerance and design and implement a novel spatio-temporal join algorithm (do not use the stock version of geopandas sjoin) based on this approximation to join individual records from both datasets. You can think of something like an adaptation of the filter-and-refine spatial join method. Filter simply means you convert each long/lat pair in each dataset to one-dimension (e.g. geohash, there are others Ubers H3, Google S2), this is known as Minimum Bounding Rectangle join (MBR-join), in other terms equi-join (geohash_AQ == geohash_Mobility) you can do this using merge() function from pandas.
      read about ``` Attribute joins ``` in [GeoPandas Merging data](https://geopandas.org/en/stable/docs/user_guide/mergingdata.html), Why?! because joining on geohash is considered an attribute-join not a direct spatial join!
      .... the problem here is that teh earth in GPS readings is flattened-out (two-dimensions x-y projection ) instead of the 3-D. What problem in geohash approximation approach this may cause. It means that two geohashes which are equal in representation may be not in proximity in real geometries (earth). What is the ```refinement``` step in this case?!. An ad-hoc solution is to take the neighborhood from each dataset and perform again an equi-join (merge) based on the neighborhood the same we've done with the geohash.
   - probably, you can start with the `NYC taxi mobility data`, that is [available online](https://github.com/IsamAljawarneh/datasets/tree/master/data), `nyc1.zip`. the target variable is `trip_distance`. From this data (in `NYC`), what is the density of taxis (vehicles) in each street?! conisder this as a starting point for the ```linear weighting method``` discussed previously.
   - **N.B.** --> start with this data by now for immediate prototyping of the system, lateron i will add more big mobility data in NYC so that you can explore and perform the final testing!
    
-------------------------------------------------
<!-- Task 3 -->
# Task 3 
- [X] **task accomplished - Excellent!**
  # `TODO:` next - Stratified-sampling 
- [x] You need to test based on `samples` taken from both `mobility` and `air-quality` data using stratified-like sampling, using geohash as your stratfification method. Then find the `routes` recommended using the same pairs of `origin` and `destination` points. Compare the results between the full data (i.e., population data) and the sampled data in terms of speed and accuracy. running-time speed means `end-end` running time, from data acquisition, street-data nx extraction, application of `join` and `sjoin`, in addition to route generation and recommendation. Accuracy means how much the sample is successful in recommending the best route based on the sample instead of the population. 
   - one way to think of this is to consider both routes (the one recommended using the sample, against the one using the original data) as trajectories and measure what is known as `trajectory similarity`. So varying the sampling fraction in the `x-axis` and the obtained `trajectory similarity` in the `y-axis` will do the trick!
      - Examples of `trajectory similarity measures` that you should use include the following:
       
         - `Euclidean Distance (ED)`, `Longest Common Subsequence (LCSS).`, `Edit Distance on Real Sequence (EDR).`
         - `Frechet Distance` ,  measures the similarity between two curves.
            - It considers the closest approach of a parameterized moving point on one curve to a parameterized moving point on the other curve.
            - It accounts for differences in speed and time.
         - `Hausdorff Distance`, calculates the similarity between two sets of points in a metric space
            - measures how far two subsets are from each other by considering the maximum distance of a point in one set to the closest point in the other set
            - particularly useful when dealing with noisy or sparse trajectories
         - Read the newly attached paper in the `literature` folder titled `Spatio-Temporal Trajectory Similarity Measures` for more information on how to use those measures for measuring similarities between trajectories!, you find it [here](https://github.com/Dr-Isam-ALJAWARNEH/ds-project-lb-context-aware-route-planner/blob/main/literature/trajectory%20similarity/trajectory%20similarity%20measure%20spatial.pdf)
         - So, in the `x-axis` you can have the `sampling fraction` (20%, 40%, 60%, 80%, 90%) and in the `y-axis` you can have the `similarity measure`, comparing trajectories resulting from original data against trajectories resulting from `sampled` data. The same strategy can also be used for comparing `routes` (i.e., trajectories) that result from recommendations using `shortest_path` method with the `weight` attribute being equal to the air quality (being that the plain particulate matters level or the one calculated as a rating by uisng the `linear weighting average`), against the routes (i.e., trajectories) that result from using the normal geographical distances as a value for the `weight` parameter. This can quantify the differences between route trajectories to measure how good is the recommendation!
-------------------------------------------------
<!-- Task 4 -->
# Task 4 
- [X] **partially completed**

- [X] **This sub-task is not essential and you can postpone it as a future work that we can further investigate together, in case you want to extend your work so that it is considered for a journal publication in a reputable venue!. Having said that, I am marking it**
   - `TODO: POSTPONED!` test with second data, and develop performance metrics
      - apply everything you have done (and you need to do in `task2`) to a second dataset, probably `NYC taxi mobility data`, that is [available online](https://github.com/IsamAljawarneh/datasets/tree/master/data), `nyc1.zip`. the target variable is `trip_distance`. You need to capture `accuracy` and `running time` as described previously.
      - You can find more data `categorized` in the following repo [datasets](https://github.com/IsamAljawarneh/datasets)

- [ ] SUB-TASK
### `IMPORTANT!` **however, you need to add the following to your code it would be great!**
   - you need to develop other performance metrics, for example, what is the difference between distances of several trips recommended by your novel system against a plain version that considers only the distance!
   - Also, you can measure the following: `the route planning effectiveness is verified by comparing the PM2.5 potential dose descending rate between the healthy route and the shortest route.` , in other terms `what is the potential dose reduction rate of the healthy route`, read more details in the reference paper newly attached titled `A short-distance healthy route planning approach`, available [here](https://github.com/Dr-Isam-ALJAWARNEH/ds-project-lb-context-aware-route-planner/blob/main/literature/reference_paper/A%20short-distance%20healthy%20route%20planning%20approach.pdf)

- [ ] SUB-TASK
### `IMPORTANT!` and also, ** you need to discuss results similar to the paper attached!**
- In sumamry, you need to obtain and discuss results similar to thoe appearing in the reference paper newly attached titled `A short-distance healthy route planning approach`, available [here](https://github.com/Dr-Isam-ALJAWARNEH/ds-project-lb-context-aware-route-planner/blob/main/literature/reference_paper/A%20short-distance%20healthy%20route%20planning%20approach.pdf)!

--------------------------------------------
<!-- Task 5 -->
# Task 5
- [X] **partially completed**

- [X] **This sub-task is not essential and you can postpone it as a future work that we can further investigate together, in case you want to extend your work so that it is considered for a journal publication in a reputable venue!. Having said that, I am marking it**
   - `IMPortant: POSTPONED` test with more than one data, add NYC taxi mobility data (for journal paper, you need tests on more than one data):
[available online](https://github.com/IsamAljawarneh/datasets/tree/master/data), `nyc1.zip`
   - You can find more data `categorized` in the following repo [datasets](https://github.com/IsamAljawarneh/datasets)

- [ ]  **This sub-task is essential**
   - start writing your paper, either for conferences or journal. For journal, use the `applied sciences` template atatched in the `target-venue` folder titled `applsci-template.dot` or ```IEEE``` template attached, or other journal template that i can attach later on. (minimum 10 pages)
   **N.B.** We may embark on another journal for submission hereafter, so, you can always move (copy/paste) your manuscript text to another journal format template!
   - or even, consider one of the following two conference (IEEE template for those conferences is attached) (minimum 6 pages)
    - [MCNA - Spain](https://mcna-conference.org/2024/committee.php)
    - [IDSTA - Croatia](https://idsta-conference.org/2024/calls.php)
1.  Refer to the papers in the `related_works` folder under `reference_paper` folder in the `literatre` folder and cite some those related works properly! Also papers in `New-April2024` folder and `trajectory similarity` folder and all papers in the `literature` folder generally.
2. [ ] Include (cite appropriately) some of the following papers! reference papers include:
    # Category A : for sampling desing and Approximate Query Processing (AQP)
    > Spatial-aware approximate big data stream processing [^2] and
    > Polygon Simplification for the Efficient Approximate Analytics of Georeferenced Big Data [^3]
    > QoS-aware approximate query processing for smart cities spatial data streams. [^4]
    > Spatially representative online Big Data sampling for smart cities. [^5]
    # Category B: for spatial join procesing
    > SpatialSSJP: QoS-Aware Adaptive Approximate Stream-Static Spatial Join Processor [^6]
    > Efficient Integration of Heterogeneous Mobility-Pollution Big Data for Joint Analytics at Scale with QoS Guarantees [^7]
    > Efficiently integrating mobility and environment data for climate change analytics.[^8]
    > Efficient QoS-aware spatial join processing for scalable NoSQL storage frameworks. [^9]
    # Category C: clustering DBSCAN
    > Efficient spark-based framework for big geospatial data query processing and analysis [^10]
 
    [^1]: Al Jawarneh, I. M., Foschini, L., & Corradi, A. (2023, November). Efficient Generation of Approximate Region-based Geo-maps from Big Geotagged Data. In 2023 IEEE 28th International Workshop on Computer Aided Modeling and Design of Communication Links and Networks (CAMAD) (pp. 93-98). IEEE.
    [^2]: Al Jawarneh, I. M., Bellavista, P., Foschini, L., & Montanari, R. (2019, December). Spatial-aware approximate big data stream processing. In 2019 IEEE global communications conference (GLOBECOM) (pp. 1-6). IEEE. [available online](https://www.researchgate.net/profile/Isam-Al-Jawarneh/publication/339562314_Spatial-Aware_Approximate_Big_Data_Stream_Processing/links/5ff45764299bf14088708888/Spatial-Aware-Approximate-Big-Data-Stream-Processing.pdf)
    [^3]: Al Jawarneh, I. M., Foschini, L., & Bellavista, P. (2023). Polygon Simplification for the Efficient Approximate Analytics of Georeferenced Big Data. Sensors, 23(19), 8178.[available online](https://www.mdpi.com/1424-8220/23/19/8178)
    [^4]: Al Jawarneh, I. M., Bellavista, P., Corradi, A., Foschini, L., & Montanari, R. (2021). QoS-aware approximate query processing for smart cities spatial data streams. Sensors, 21(12), 4160. [available online](https://www.mdpi.com/1424-8220/21/12/4160)
    [^5]: Al Jawarneh, I. M., Bellavista, P., Corradi, A., Foschini, L., & Montanari, R. (2020, September). Spatially representative online Big Data sampling for smart cities. In 2020 IEEE 25th International Workshop on Computer Aided Modeling and Design of Communication Links and Networks (CAMAD) (pp. 1-6). IEEE.[presentation available online](https://isamaljawarneh.github.io/talks/CAMAD20.pdf)
    [^6]: Al Jawarneh, I. M., Bellavista, P., Corradi, A., Foschini, L., & Montanari, R. (2023). SpatialSSJP: QoS-Aware Adaptive Approximate Stream-Static Spatial Join Processor. IEEE Transactions on Parallel and Distributed Systems. [available online](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10309986)
    [^7]: Al Jawarneh, I. M., Foschini, L., & Bellavista, P. (2023). Efficient Integration of Heterogeneous Mobility-Pollution Big Data for Joint Analytics at Scale with QoS Guarantees. Future Internet, 15(8), 263. [available online](https://www.mdpi.com/1999-5903/15/8/263)
    [^8]:Al Jawarneh, I. M., Bellavista, P., Corradi, A., Foschini, L., & Montanari, R. (2021, October). Efficiently integrating mobility and environment data for climate change analytics. In 2021 IEEE 26th International Workshop on Computer Aided Modeling and Design of Communication Links and Networks (CAMAD) (pp. 1-5). IEEE.[presentation available online](https://isamaljawarneh.github.io/talks/CAMAD21.pdf)
    [^9]:Al Jawarneh, I. M., Bellavista, P., Corradi, A., Foschini, L., & Montanari, R. (2020). Efficient QoS-aware spatial join processing for scalable NoSQL storage frameworks. IEEE Transactions on Network and Service Management, 18(2), 2437-2449.[available online](https://isamaljawarneh.github.io/pubs/TNSM3034150.pdf)
    [^10]: Aljawarneh, I. M., Bellavista, P., Corradi, A., Montanari, R., Foschini, L., & Zanotti, A. (2017, July). Efficient spark-based framework for big geospatial data query processing and analysis. In 2017 IEEE symposium on computers and communications (ISCC) (pp. 851-856). IEEE. [available online](https://www.academia.edu/download/55478212/08024633.pdf)
-------------------------
<!-- Task 1 -->
# Task 1 
- [X] **task MOSTLY accomplished - Excellent!** 
- [X] run the example starting code and familiarize yourself with some geosaptial processing techniques, including:
   - sampling
   - spatial join
   - geo-visualization
   ### ```attention``` You have to perform  this task!!! **sub-task accomplished - Excellent!** 
- [X], **i will consider this sub-task accomplished - Excellent!** start by performing Exploratory Data Analytics (EDA) for the data > for example - historgrams to study the distribution of data (you have three sensors) - `Kernel Density (univariate, aspatial)` - get insights from the following: - [02_geovisualization](https://darribas.org/gds_scipy16/ipynb_md/02_geovisualization.html) - [Exploratory Spatial Data Analysis (ESDA)](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html) - [NYC Data](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter02/NYC%20Data.ipynb) - [Performing Spatial operations like a Pro](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter03/Chapter3.ipynb) such as `Spatial join`
   > also,
   > - Exploratory Spatial Data Analysis (ESDA) [example](https://darribas.org/gds_scipy16/ipynb_md/04_esda.html), such as `Spatial Autocorrelation`
   > - Exploratory Spatial and Temporal Data Analysis (ESTDA), [example](https://darribas.org/gds_scipy16/ipynb_md/05_spatial_dynamics.html), such as `Spaghetti Plot`, `Kernel Density (univariate, aspatial)`, `Markov Chains`, and `Spatial Markov`, [Spatial Autocorellation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb), and [GLobal Spatial Autocorrelation](https://github.com/PacktPublishing/Geospatial-Data-Science-Quick-Start-Guide/blob/master/Chapter04/Chapter4.ipynb)
- [X]  **sub-task accomplished - Excellent!** Find the example notebook titled `shortest-path.ipynb`.
   > You need to find the street network of NYC and join (`spatial join`) the sensor's reading you have in the .csv file (air quality sensor's readings collected from NYC), then you will have a new file containing the readings and to which street (edge in OSMNX terms) they belong each, then you can compute, for example, the average PM10 value in each street segment, then this would be the `weight` that you can pass to the `shortest_path` function in `osmnx`. This is not binding!!!, depending on your `EDA` and `ESDA` and `ESTDA`, you decide what is the `weight` that you want to pass to the `shortest_path` function in `osmnx`.
- [X]  **sub-task accomplished - Excellent!**, Then, given an origin point and a destination, > what is the `shortest path` that minimizes the total `PM10` exposure. Imagine a scenario where a lady dweller is walking a baby on a trolley and she is trying to avoid the areas that are most polluted by navigating your map that recommends shortest path in terms of less pollution (less exposure to PM10, in total!) -
  
NEW! 25 March 2024

- [X] **sub-task accomplished - Excellent!**. You next task, is to extract street segments in NYC in the form of geojson (use the attached examples as a jumping off point), geojson file  will contain geometry columns consisting of a linestring for each street segment. 
   - For each point in the AQ data csv file, find the corresponding street segments which is the nearest. You need to use [GeoDataFrame.sjoin_nearest](https://geopandas.org/en/stable/docs/user_guide/mergingdata.html). Explore it in details [sjoin_nearest](https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoDataFrame.sjoin_nearest.html#geopandas.GeoDataFrame.sjoin_nearest). By this we know to which street each point (AQ reading) belongs. 
   - Find the shortest path based on the pm25 as the weight. in the ```shortest_path(G,                         orig_node,    dest_node,        weight='length')``` change the weight to ```pm```. Change the ```method``` parameter to ```bellman-ford``` and compare the results, combination of two algorithms (distance + pollution level) compare ```bellman-ford``` and ```dijkstra``` in terms of `Kilometer distance`, remeber both of them give us optimized shortest path in terms of ```pm``` compare which one is guranteed `less kilometers` (a combination).
- [ ] Make a page similar to the following [green path](https://green-paths.web.app/) using [leaflet](https://leafletjs.com/)
- [X] **this sub-task is not essential, you can skip it**. BONUS point: use a a ```linear weighting method```  to construct a new weight that is based on both distance and pm, and recommend route based on that!

 **_Team members_**

- [Eisa Sajwani](https://github.com/EisaSajwani)
- [Eisa Ali Alsaadi](https://github.com/eisaaliedu)
- [Dr. Isam Al Jawarneh](https://isamaljawarneh.github.io/) (Supervisor)
