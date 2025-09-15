# UC5 - Validation of Phytosociological Methods through Occurrence Cubes



## Introduction



Use Case 5 investigates how integrating species occurrence data with environmental variables can improve habitat mapping accuracy across Europe. A central focus of this use case is the exploration of the usefulness and reliability of GBIF data, particularly data from citizen science initiatives and museum collections, which are often overlooked or underrepresented in traditional ecological modelling efforts.

By leveraging occurrence records from the Global Biodiversity Information Facility (GBIF)—spanning scientific publications, citizen-contributed observations, and curated museum specimens—Use Case 5 aims to evaluate the potential of these diverse data sources to enhance habitat classification methods. This work challenges conventional modelling approaches by explicitly incorporating non-traditional data into machine learning (ML) models, assessing how well they align with and refine existing habitat maps, such as those defined by the European Nature Information System (EUNIS).



## Research Questions



Which environmental factors influence the distribution and community formation of plant species in European habitats (S22)?

Can integrating species occurrence data from databases like GBIF and environmental factors retrieved from EO sources improve habitat prediction accuracy, especially within the context of the EUNIS system?

How do the predictions of species distribution compare with existing habitat maps, and where do discrepancies arise?





## Workflow



### Short Summary of Workflow

The UC5 workflow begins with retrieving occurrence data for diagnostic species of the EUNIS Habitat S22 from GBIF, alongside environmental and topographical data from various Earth Observation (EO) sources. The data is then pre-processed—filtered, cleaned, and structured into occurrence data cubes. To address the presence-only nature of GBIF data, pseudo-absence points were generated using a disc buffer method and merged with the presence data to form complete datasets for modelling.

Next, species distribution models were developed using ensemble machine learning techniques. The resulting predictions of the eight main species of the study case habitat (S22) were aggregated and validated using the vegetation plots from EVA. Lastly, they were evaluated by comparing them against the EUNIS habitat probability map.



### 1) Data retrieval 

The UC5 workflow began with the retrieval of species occurrence data from GBIF, which includes distribution records derived from herbarium collections, citizen science initiatives, and biodiversity surveys, all containing spatial and temporal coordinates. Environmental variables were obtained from multiple Earth Observation (EO) sources, including Copernicus, CHELSA Bioclim, and WorldClim. These datasets provide a range of climatic and topographic variables relevant for habitat modelling, such as temperature, precipitation, elevation, slope, TWI, HLI, TPI, and aridity index (AI).

Data ingestion was carried out locally via APIs rather than through the FAIRiCUBE infrastructure. The temporal range of the collected data spans from 1980 to 2024, focusing on the spring and summer months.



### 2) Environmental and Species Data Filtering

Data preprocessing involved several crucial steps to clean and filter the raw datasets. Species occurrence records were filtered to remove duplicate entries, records with uncertain taxonomy, high uncertainty in coordinates (greater than 500m), and incorrect or missing coordinates, ensuring that the remaining data accurately represented the species’ true distribution.



### 3) Processing Steps and ML Applications

Once the occurrence  data were cleaned, the following steps were undertaken:



* Data Cube Integration: Processed species occurrence data were integrated with environmental variables to create data cubes, which allow for the spatial and temporal relationships between species and their habitat drivers to be analysed. These cubes serve as the primary data structure for the machine learning models.



* Pseudo-absence Generation: To improve model accuracy, pseudo-absence points were generated using a buffer-based random sampling method with a 100 meter radius. This approach ensures a balanced dataset by generating pseudo-absence points outside the buffer zones surrounding each presence location.



* Ensemble Modelling: Species distributions were predicted using an ensemble approach that combines individual models such as Generalized Linear Models (GLM), Generalized Additive Models (GAM), and Random Forest (RF). To balance spatial coverage and computational efficiency, predictions were made at two resolutions: 1 km for the broader European scale and 100 m for the more detailed Alpine region.  Each model was trained on 90% of the data and evaluated using the True Skill Statistic (TSS), derived from 10-fold cross-validation stratified by presence–absence data. Following performance evaluation, individual model predictions were combined into a single species distribution map using weighted averaging, where each model’s contribution was proportional to its TSS score—giving greater influence to more accurate models. Lastly, the predicted species distributions were aggregated in a distribution map for the Habitat S22.



* Validation with EVA data:  Model predictions were validated using the EUNIS-ESy habitat distribution maps derived from the EVA database, which served as an independent reference for the Habitat S22 at 1 km resolution.



* Comparison with EUNIS Maps: The predicted distribution outcomes (1km, 100m) were compared to the existing EUNIS probability map for the Habitat S22 to assess discrepancies and validate the alternative methodology for habitat prediction.





## Solutions/Results

Following the workflow built by the Use Case, it is possible to produce refined habitat distribution predictions that more accurately reflect plant species distribution in relation to environmental variables. The outputs include scripts to produce: data cubes that integrate species occurrence and environmental data, as well as predictive models for habitat distribution mapping. These outputs are openly available, allowing for reproducibility and further application in biodiversity monitoring, conservation, and museum collections curation.





## Resources



The full methodology, including code and documentation, are available in the GitHub repository for UC5. 

Key resources include:

Data Sources:

* Species occurrence datasets: GBIF (https://www.gbif.org)

* Environmental data: Copernicus, Chelsa Bioclim, WorldClim

* EUNIS Habitat classification system (map S22)





## Software and Tools:

* R (https://www.r-project.org/)

Scripts: 

* GBIF data retrieval and pre-processing

* Data cube creation

* Pseudo-absence data creation

* Ensemble model

* Outputs comparison


