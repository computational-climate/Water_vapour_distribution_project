READ ME 

This repository contains all the code made/used during the project on tracer-enabled simulation, focused on « how is water vapour recently evaporated from land distributed within the atmosphere, and what are its regional spatio-temporal patterns »

1. Project purpose  Overview:
Among the most dominant greenhouse gases, water vapour is often forgotten however it accounts for 50% of the present day greenhouse effect. Over the past centuries, the role of land in the atmospheric moisture (notably via evapotranspiration) has been discussed. As this essential element of the planetary system is lacking a global 3D baseline regarding its land-sourced part,  this study will analyse the spatial and temporal distribution of the water vapour recently evaporated from different land over 25 years, between 1980 and 2004, using simulations made by a complex global circulation model iCESM, providing high resolution 3D moisture tracking via a Lagrangian approach with isotopes as tracers. These 12 tracers allow a regional analysis 

2. Model Overview:
The model used for this project is iCESM, The model has a nominally 2-degree resolution on a f19_g16 grid with 30 pressure layers.The SST are the Hadley centre sea surface temperature reconstruction(  "AMIP") and the sea ice is also the prescribed one from the sst dataset.
The models used are:
- CLM4 (Satellite Phenology prescribed leaf area index, 1850 vegetation distribution) 
- CAM5 , with 12 isotopes used as tracers. 
- RTM river 
- No land ice nor wave models

3. Simulations Overview:
A single simulation is ran (‘amip’), for 26 years (1979-2005). The collected data are monthly and the first year is droppedto allow the spin up of the model. Water vapour is studied with a Lagrangian approach, by using 12 tracers (11 regional and 1 global) for the different planetary land regions to locate the land source of the atmsopheric moisture
The tracers are the following :

All Land 
North Pole (60°N to 90°N)
Northern mid-latitude (20°N to 60°N)
•     North America (180°W to 20°W)
•     Europe and northern Africa (20°W to 60°E)
•     Eastern Asia (60°E to 180°E)
Tropics / low latitudes (-20°N to 20°N)
•     Central and South America (180°W to 20°W)
•     Central Africa (20°W to 60°E)
•     Maritime continent (60°E to 180°E)
Southern mid-latitude (-20°N to -60°N)
•     South America (180°W to 20°W)
•   South Africa (20°W to 60°E)
•     Australia (60°E to 180°E)
South pole (-60°N to -90°N)


4. Python files contents:
·      Sanity_checks :
This file allows to verify the coherence of the result, via several checks. It also compare the impact of integration functions and store intregrated data  in ‘Vert_int_output’ for all the tracers (last cell).
NB : It is NECESSARY to run this file at least once (or to copy the cell and run it in another file) since the other files are calling the stored data

·      Spatial_dimension_focus:
This file contains plots regarding the spatial distribution. After the initial setup, it has 3 parts in the data-analysis :
-       General spatial distribution : map and vertical repartition for each tracer (time mean)
-       Pressure focus : different plots regarding the distribution in the vertical dimension
-       Latitude focus : different plots regarding the latitude dimension

·      Temporal_analysis:
This file focuses distributions over time, including map for different years, Hovmöller plots and evolutions of moisture with time

·      ENSO_pattern :
This file is exploratory : it contains different comparison between El Nino and la nina years (such as maps or latitude distribution)
(such as maps or latitude distribution)
It also contains calculus of the ONI (code from Marysa Laguë) and correlation of each tracer with it

·      Raw_data_EOF :
This files contains EOFs (PCA) of the raw data for the 12 tracers. It represent the 3 first patterns : Spatial map (2D), PC and correlation of the PC with ONI for each tracer. The first mode generally matches the annual cycle. The second can potentially be correlated with ONI.
The EOFs are also done in 4D to have the vertical pattern. Caution : the 4D EOFs require several nodes to run.

·      Anomaly_EOF :
This file reproduces the last one, but to avoid the Seasonal cycle, the EOF are done with anomaly data.

·      Additional_EOF :
This file contains additional EOFs for other variables (temperature, precipitation, evaporation).

·      Annual_variability :
This file focuses on the Annual profile of the water vapour and its interannual variability for the different regions. It also provides a table with some statistic data to compare the tracers.