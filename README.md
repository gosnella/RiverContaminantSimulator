# RiverContaminantSimulator

## Description
The RiverContaminantSimulator is a tool for simulating the behaviour of contaminants within a river network. This project demonstrates how contaminants disperse and propagate within the water system. The data used to develop the simulation were released by Thames Water and Ordnance Survey.

## Data

* [OS Open Rivers](https://www.ordnancesurvey.co.uk/products/os-open-rivers): contains over 144,000 km of water bodies and watercourses map data. These include freshwater rivers, tidal estuaries and canals
* [Thames Water storm discharge annual reports](https://www.thameswater.co.uk/about-us/performance/river-health/storm-discharge-data):  contains the number of times storm overflows were active and for how long for the years 2021 and 2022
* [Thames Water live activity](https://data.thameswater.co.uk/s/): API portal for retrieving the most recent data on the treatment site activity. Contains the location of the ~470 treatment sites, in addition to the most recent duration of discharge

## Software

* Neo4j (NoSQL): storing, managing, and querying. Python used for compiling Cypher query language
* Oracle VM (Linux): optimise computational performance
* Azure DevOps/GitHub: collaborating and managing tasks
* Python: develop the simulation
  * Plotly: visualise the simulation
  * Pandas, NumPy: data manipulation
  * imageio: generate the gif
  * os: interaction with operating system
  * pytest: unit testing

## Data processing 

* Transform the British National Grid (BNG) coordinate reference system to the Geographic Coordinate System.
* Reverse sections of the river
* Impute missing sections of the river
* Remove sections of the river that were not connected to a treatment site
* Approximate the origins of the contaminant. This was performed by identifying the closest point between the rivers and the treatment sites using the Haversine distance
* Approximating river capacity so that when rivers merge contaminant gets diluted. Merging of contaminated paths results in accumulation of contaminant

## Visualisation

* Inactive sites are illustrated as black dots and are land based
* Active sites are illustrated as larger red dots and discharge a random amount of contaminant
* Contaminant levels are low (yellow), medium (amber), and high (red)
* River width increases with capacity

## Practices

* Descriptive functions and variable names
* Descriptive docstrings with variable types specified
* Default arguments provided
* Comments where necesssary
* Functions properly tested
  
## Assumptions

* If a river splits in two, contaminant goes down a single path (depth-first search). Only few paths split and re-join
* Contaminants move at different speeds
* River paths remain contaminated until the simulation ends
* Dishcarge locations are the nearest points on the river to the treatment sites
* All rivers start with a capacity of 1
* Sites are contaminated at random
* A random amount of contaminant is released
* Contaminant concentration is affected by path capacity and merging contaminant levels
  
## Value:

* Enable utility companies to identify the extent to which the river is contaminated.
* Identify regions of the network that are either saturated to take action, or contaminant-free to indicate safe zones (fishing, swimming, property purchase).
* Advise the closures of treatment sites so that contaminant levels remain below the regulatory requirements

## Versatility:

* Potential to apply to other domains:
  * Logistics
  * Food contaminantion
  * Animal migration
  * Electricity/telecommunications network failure