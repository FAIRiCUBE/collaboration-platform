<<<<<<< HEAD:docs/use_cases/urban_climate.md
# Urban adaptation to climate change - UC1

The aim of this use case is to provide comprehensive data on urban adaptation to climate change, offering a clear picture of the current situation.

A persistent challenge in developing effective adaptation strategies is the complexity of integrating and analyzing heterogeneous datasets with varying formats and quality. The UC1 approach addresses this issue through two key components: a process to **harmonize diverse datasets into structured data cubes**, and a comprehensive **toolkit for their analysis and presentation**. These tools support UC applications at multiple scales.

At the **European level**, they help identify cities with similar characteristics and analyze how different factors influence their adaptation capacity. At the **local level**, specialized "city cubes" serve specific goals, as demonstrated through collaborations with Luxembourg City on managing invasive plant species and support provided to Vienna city initiatives.

## EU level - City features collection

### Research questions

* What are commonalities of and differences between cities in terms of their situation about climate adaptation considering comparable European data sets from various sources (Copernicus, ESTAT)?  Can we identify groupings of cities with similar conditions with respect to different climate pressures (e.g. heat islands, air quality…) 
* Can we identify the impacts of certain measures in cities? E.g., what does it mean to increase the urban tree cover as requested by European policies?  

### Workflow 

![Processing workflow - EU application](../images/uc1_workflow_eu.png)

## Data and ingestion

| Dataset name | Description | Link to Metadata
|---|---|---|
| GISCO Urban Audit | Provides harmonized statistical data on quality of life in European cities, including demographics, housing, health, and environment. | https://ec.europa.eu/eurostat/web/gisco/geodata/statistical-units/urban-audit |
| Copernicus DEM | A high-resolution Digital Elevation Model representing Earth's surface, including buildings and vegetation, available in 10m, 30m, and 90m resolutions. | https://doi.org/10.5270/ESA-c5d3d65 |
| Environmental Zones | A classification of Europe into ecological zones based on environmental stratification, supporting biodiversity and land management. | https://sdi.eea.europa.eu/catalogue/idp/api/records/6ef007ab-1fcd-4c4f-bc96-14e8afbcb688 |
| CLMS HRL Imperviousness | Maps the degree of soil sealing (e.g., roads, buildings) across Europe, supporting urban planning and environmental monitoring. | https://land.copernicus.eu/en/products/high-resolution-layer-imperviousness |
| CLMS HRL Tree Cover Density | Provides percentage-based tree cover data across Europe, useful for forest monitoring and carbon accounting. | https://land.copernicus.eu/en/products/high-resolution-layer-tree-cover-density?tab=main |
| Urban Atlas (CLMS) | Detailed land cover and land use data for Functional Urban Areas in Europe, supporting urban planning and policy. | https://doi.org/10.2909/fb4dffa1-6ceb-4cc0-8372-1ed354c285e6 |
| Thermal Comfort Indices (ERA5) | Derived from ERA5 reanalysis, this dataset includes indices like UTCI and MRT to assess human thermal stress in outdoor environments. | https://doi.org/10.24381/cds.553b7518 |
| Eurostat Urban Audit (Socio-economic) | Offers socio-economic indicators for European cities, including data on population, education, employment, and income. | https://ec.europa.eu/eurostat/cache/metadata/EN/urb_esms.htm |


### Processing steps and ML applications

TODO

### Solution(s) 

TODO


### Resources 

An example Jupyter Notebook is provided by UC1: [Getting started with FAIRiCube Hub](https://github.com/FAIRiCUBE/uc1-urban-climate/blob/master/notebooks/demo/demo_processing.ipynb)

## Local level: invasive alien plant species

At local level, the focus was on leveraging earth observation data cubes to monitor invasive plant species. These research questions were developed in collaboration with the Environment delegate of Luxembourg City administration:

### Research questions

* Can we identify correlations between plant neophytes’ presence and spatial and environmental factors in urban areas? 
* Can we identify patterns of neophytes spread, and how they affect sensitive areas? 

### Workflow 

![Processing workflow - local application](../images/uc1_workflow_local.png)

### Data and ingestion

Table 2 lists the input data sets used for this application. All the datasets were pre-processed to match the species distribution model requirements. Shadow index and Topographic wetness index were derived from Luxembourg DEM; gridded land cover was obtained by rasterizing the land cover map, which is a vector dataset; Soil acidity, soil nitrogen and temperature were extracted (clipped) from EU wide datasets, reprojected and regridded to match the target CRS (LUREF) at 10m resolution. Most of the preparatory work has been carried out in EOXHub using Python, except for the generation of the Shadow index and Topographic wetness index maps, which was done in QGIS. 

| Dataset name                             | Description                                                                                                                                                                                                      | FAIRiCUBE STAC Catalog link                                                                                                                                                                                     |
| ---- | ---------------------------- | --------------------------- |
| Shadow index                             | The normalized shadow index quantifies the duration of shadow within 10x10m area.                                                                                                                                | [catalog.eoxhub.fairicube.eu/collections/index/items/shadow_index_city_of_luxembourg](https://catalog.eoxhub.fairicube.eu/collections/index/items/shadow_index_city_of_luxembourg?.language=en)                 |
| Topographic wetness index                | The TWI models soil moisture from the digital terrain model based on the size of the upslope contributing area (how much water flows to a point) and the local slope (how likely water is to stay or flow away). | [catalog.eoxhub.fairicube.eu/collections/index/items/wetness_index_city_of_luxembourg](https://catalog.eoxhub.fairicube.eu/collections/index/items/wetness_index_city_of_luxembourg?.language=en)               |
| Average monthly air temperature for 2017 | Average monthly air temperature for 2017 extracted from the Copernicus Climate Data Store. The data were generated using the urban climate model UrbClim.                                                        | [catalog.eoxhub.fairicube.eu/collections/index/items/air_temperature_city_of_luxembourg_2017](https://catalog.eoxhub.fairicube.eu/collections/index/items/air_temperature_city_of_luxembourg_2017?.language=en) |
| Soil acidity                             | Soil Chemical properties based on LUCAS 2009/2012 soil surveys.                                                                                                                                                  | [catalog.eoxhub.fairicube.eu/collections/index/items/soil_ph_city_of_luxembourg](https://catalog.eoxhub.fairicube.eu/collections/index/items/soil_ph_city_of_luxembourg?.language=en)                           |
| Soil Nitrogen                            | Soil Chemical properties based on LUCAS 2009/2012 soil surveys.                                                                                                                                                  | [catalog.eoxhub.fairicube.eu/collections/index/items/soil_nitrogen_city_of_luxembourg](https://catalog.eoxhub.fairicube.eu/collections/index/items/soil_nitrogen_city_of_luxembourg?.language=e)                |
| Land cover                               | Land Cover of the City of Luxembourg                                                                                                                                                                             | [catalog.eoxhub.fairicube.eu/collections/index/items/land_cover_city_of_luxembourg](https://catalog.eoxhub.fairicube.eu/collections/index/items/land_cover_city_of_luxembourg?.language=en)                     |



### Processing steps and ML applications

TODO

### Solution(s) 

TODO


### Resources 

An example Jupyter Notebook is provided by UC1: [Getting started with FAIRiCube Hub](https://github.com/FAIRiCUBE/uc1-urban-climate/blob/master/notebooks/demo/demo_processing.ipynb)

## Partners

space4environment and Stiftelsen Norsk Institutt for Luftforskning, Norwegian Institute for Air Research.



=======
# Urban adaptation to climate change - UC1


This use case covers the priority “climate change” with a specific focus on the adaptation of cities to climate change. The use case would also be able to link up with other priority actions, i.e., “zero pollution” and “biodiversity”. Even the action items “deforestation” and “compliance assurance” might have a link.

## Research questions

* Do the currently available European data help cities in being appropriately informed about climate change and its impact on cities?
* Can big data (historical, real-time, and modelled forecast spatial data) and ML approaches help European cities to prepare for the impacts of climate change and take adaptive measures/make informed decisions?
* In how far can datacubes enable local, regional, national, and European decision-makers to achieve the goals of the European Green Deal?
* Does the European Green Deal data space provide the best possible means to collect, store and provide European data on climate change impacts on cities?

## Workflow 
dd

## Data and ingestion

dd

## Processing steps and ML applications

dd

## Solution(s) 

dd


## Resources 

link to data, github, paper, further documentations

An example Jupyter Notebook is provided by UC1: [Getting started with FARiCube Hub](https://github.com/FAIRiCUBE/uc1-urban-climate/blob/master/notebooks/demo/demo_processing.ipynb)

## Partners

space4environment and Stiftelsen Norsk Institutt for Luftforskning, Norwegian Institute for Air Research



>>>>>>> bc6095b (change file UC name):docs/use_cases/uc1_urban_climate.md
