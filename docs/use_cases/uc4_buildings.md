# UC4 - Spatial and temporal assessment of neighbourhood building stock

The purpose of this use case is to focus on the potential impacts of building stocks on the material use and greenhouse gas emissions over time. This use case is geared towards two of the EGD priority actions (i.e., climate change and circular economy) emphasizing the need to enhance energy and resource efficiency in the building construction sectors, specifically during the renovation activities.

## Research questions

* Are enough data available to have a spatial estimation of building materials availability and energy performance of buildings?
* To what extent can datacube infrastructure support actors, researcher, stakeholders, etc. to tackle the Green Deal priority action plans related to climate change and circular economy?
* How efficiently and effectively can datacube infrastructure be scaled up to cover building stock at regional or national level?
* Can datacube infrastructure knowledge be easily transferred and reproduced for other types of infrastructure (i.e., green, blue, and grey infrastructure)?

## Workflow 

The UC4 workflow is designed to construct a scalable and interoperable model of the residential building stock in selected European cities, focusing on spatial and temporal assessment of energy demand and material usage. The pipeline begins by assembling and aligning multiple data streams: 2D building footprints from OpenStreetMap and municipal cadastral systems, vertical elevation data from Digital Surface Models (DSM) and Digital Terrain Models (DTM), and semantic attributes (e.g., construction year, building typology) from city-level records.

A Canopy Height Model (CHM) is computed by subtracting DTM from DSM, yielding per-building height estimates, which are then combined with footprint area to derive building volumes. These geometries serve as the structural foundation for energy demand estimation using the EPISCOPE/TABULA framework, which supports three renovation scenarios—baseline (as-built), intermediate, and deep renovation—allowing exploration of progressive retrofitting interventions.

The entire pipeline is modular, with outputs formatted as GeoTIFF raster and vector data layers were appropriate and ingested into a spatial-temporal data cube hosted on the FAIRiCUBE platform (EOXHub). These layers include raw inputs (e.g., height rasters), intermediate transformations (e.g., wall adjacency masks), and model results (e.g., energy demand surfaces), supporting cross-use-case interoperability and reproducibility.

![Figure 1 – Workflow overview](workflowuc4.png)

## Data and ingestion

No automated ingestion system was deployed. Instead, a hybrid strategy was used for data acquisition: datasets were either fetched dynamically using public APIs (e.g., Overpass API for OSM building tags) or downloaded manually from authoritative sources such as Copernicus Land Monitoring Services and national geospatial portals (e.g., for DSM/DTM data in .xyz or GeoTIFF format).

Once curated, data were uploaded to EOXHub and tagged with appropriate metadata, enabling FAIR-compliant sharing across the consortium. Cities currently covered include Oslo, Rennes, Barcelona, Vienna, and Luxembourg. Uploaded layers span a variety of formats: vector data (GeoJSON for footprints), raster height grids (DSM/DTM), tabular archetype data (EPISCOPE profiles), and orthophotos. Ingestion included spatial pre-processing such as cropping to municipal boundaries, reprojection to common CRS, and resampling for grid alignment.

Special emphasis was placed on data harmonization, particularly for aligning OSM polygons with raster grids, and integrating local cadastral attributes where possible to fill gaps in public data (e.g., building use types and year of construction).

## Processing steps and ML applications

Processing in UC4 combines rule-based geospatial analytics with supervised machine learning (ML), structured into a cascade of tasks:

- Geometric Enrichment: Building heights are inferred from CHM or approximated via auxiliary sources such as OSM storey counts, with three tested height estimation techniques:

	1. Storey multiplier: multiplying number of floors (where known) by a calibrated mean ceiling height;

	2. Geoclimate ML model: a Random Forest regressor trained on morphological features extracted from OSM and validated using BDTopo reference datasets;

	3. DSM–DTM subtraction: direct raster-based height estimation from public elevation models.

- Semantic Modelling: Each building is assigned a typology based on EPISCOPE/TABULA classifications using inputs such as building age, type, and geometry (volume, floor area). This determines default thermal properties and renovation trajectories.

- Energy Demand Estimation: Following the EPISCOPE methodology, UC4 computes heating energy demand via a thermal balance model accounting for:

	- transmission losses (U-values of walls, roofs, floors, windows),

	- ventilation heat exchange,

	- internal and solar gains,

	- and correction for adiabatic surfaces (shared walls in dense housing clusters).

- ML-enhanced Inference:

	- Height Estimation via CNN: A rooftop height estimation model was trained using >26,000 cropped orthophotos in Vienna. VGG16 CNN architecture extracted image features, followed by XGBoost regression and LightGBM classification (binary and four-class roof height).

	- Gap-filling: Construction year prediction via XGBoost was tested where cadastral records were unavailable.

- Embodied Carbon Assessment: Archetype-specific material intensities (kg/m²) from EPISCOPE were combined with life-cycle emission factors (sourced from https://co2data.fi) to estimate GHG emissions embedded in the building fabric (scope 3).

All processing is scripted in Python using open-source geospatial and ML libraries (e.g., GeoPandas, Rasterio, TensorFlow, XGBoost). Outputs are rasterized into consistent 10 m resolution layers and stored in the FAIRiCUBE data cube for spatial querying and aggregation.

## Solution(s)

UC4 delivers a robust and transferable urban modelling framework for assessing energy performance and circularity potential in residential buildings. Its core strengths include:

- Low threshold input requirements (LoD1 geometry), allowing broad applicability across European cities;

- Modular architecture, supporting substitution of data and methods at each stage;

- Integrated rule-based and machine-learning components, enabling gap-filling and inference from partial data;

- Support for prospective analysis, including neighbourhood-level retrofit prioritization using optimization routines aligned with the EU Renovation Wave.

The framework has been validated and deployed in multiple cities (Oslo, Rennes, Barcelona), each with varying data availability, confirming resilience against heterogeneity in urban data ecosystems. Intermediate products, such as canopy height rasters or energy mix maps, are also reusable by other FAIRiCUBE use cases or external platforms.

## Resources

| Category      | Description 	|
| --- 		| -------- 	|
| [GitHub](https://github.com/FAIRiCUBE/uc4-building-stock ) 	| OpenSource Python code and notebook repository |
| [Zenodo Data Repository](https://zenodo.org/search?q=fairicube&f=resource_type%3Adataset&l=list&p=1&s=10&sort=bestmatch) 	| Published data sets with DOIs|
| [FAIRiCUBE Data catalog](https://catalog.eoxhub.fairicube.eu/search) 	| Data and meta data records including preview 	|
| [Metadata](https://fairicube-kb.epsilon-italia.it/) 	| Querry tool for meta records  	|
| [Scrollytelling](https://uc4.fairicube.nilu.no/) 	| Brief data and use case overview |
| Publications 	| tba	|

Software stack:

- Geospatial: GeoPandas, QGIS, GDAL, Rasterio, osmnx

- ML/AI: TensorFlow (VGG16), XGBoost, LightGBM, joblib

- Data: GeoJSON, GeoTIFF, shapefiles, JPEG, CSV

- Deployment: FAIR-compliant publication on EOXHub; reusable datasets for cross-city application

## Partners
NILU, Climate and environmental research institute (https://nilu.no/)
