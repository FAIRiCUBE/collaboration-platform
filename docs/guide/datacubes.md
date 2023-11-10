# Datacubes

The concept of multidimensional datacubes can help overcome many challenges with respect to performance, scalability, interoperability, semantics, sampling, geo-referencing, and readiness for ML applications.

While initial effort is required to transform existing point and vector sources to multidimensional grid formats and harmonize domain semantics, these formats’ discrete spatio-temporal basis facilitates alignment and is advantageous for automated processing.
Depending on the technology used, creating datacubes can be done either through referencing existing archive files generating “virtual cubes” for users or importing (i.e., copying) with re-gridding, which requires some computational efforts as a pre-processing step. In both cases, the user can directly focus on the data analysis and interpretation step.

Each dimension of a datacube can represent a different property, integrating data from diverse sources across standard dimensions such as space and time; all this data is typically hosted in a single or multiple cloud environments. As long as the spatio-temporal dimensions of all component sources can be aligned, additional dimensions pertaining to the properties provided in these data sources can be added, and each grid point of the datacube can be populated with a variety of physical, biological, socio-economic, geographical, etc. properties.

Subsets of this data (data windows or ranges) can be defined and accessed from a cloud-based data hosting service. Subsequently, these can be processed and transformed to spatial features and indicators, providing insights on a wide range of properties not necessarily contained within the originally accessed data. These outputs can then be directly visualized or passed on down the pipeline for additional processing.
Aggregating data over individual dimensions of the cube and processing across dimensions is solved efficiently by the underlying datacube engine. These cube capabilities providing discretely structured and aligned data allow for straightforward and efficient application of ML algorithms. For large spatio-temporal datasets common in Earth Observation, raster formats aligned with common datacubes appear to be the most appropriate form of data storage/handling/processing.


FAIRiCUBE provides a growing list of relevant variables for Earth System Science. Most of them have been derived from Earth Observation, but the compilation also includes model or re-analysis data if deemed useful.<br>
FAIRiCUBE is very grateful to all data owners for kindly providing the data sets and allowing us to process, and redistribute them free of charge (unless otherwise noted).<br>
All datacubes generated and distributed by FAIRiCUBE come without any warranty, neither from the owners, from the FAIRiCUBE, nor from ESA.

During ingestion into the FAIRiCUBE, data sets are typically transformed in space and time to fit to the common grid of the data cube, a process that necessarily modifies the original data. If you are looking for the original data, please follow the links within the dataset attributes for each variable and contact the data owners.

To access the documentation of available datasets, please have a look in the [FAIRiCUBE Catalog](https://catalog.eoxhub.fairicube.eu/).

