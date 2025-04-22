 # Drosophila Genetics - UC3

Combining earth observation and genomics data to study the evolutionary history of the fruit fly Drosophila melanogaster.

In our “Drosophila genomics” use case, we take advantage of comprehensive earth observation data for climate and land use available in the public domain. We will combine environmental data with genomic information of fruit fly DNA samples from more than 300 European Drosophila melanogaster populations that were densely sampled through time and space by [DrosEU](https://droseu.net), our partner consortium. We are developing tools that facilitate extracting information for sample coordinates from gridded datasets to identify links between genetic variation along the whole Drosophila melanogaster genome and environmental variation.

This approach will allow to identify genes that are putatively under selection and involved in adaptation to environmental change. Using machine learning approaches, we further aim to identify combinations of environmental factors that may influence the genetic diversity in natural populations which will help us to better understand the impact of climate change on the accelerating biodiversity crisis.



## Research Questions

1) How....?
2) In which...?
3) ....?

## Workflow

- Genomic Data: We work with genomic data from Drosophila melanogaster at population level, available at [DEST.bio](https://dest.bio/). This genomic data is availbale at a common data format called "Variant Cal Format" or short VCF. From these VCF files, we generate so-called Allele Frequencies for each population.

- Environmental Data: Environmental data is available from various sources, matching our regions and times of interest. We used FAIRiCUBE infrastructure to access earth observation and environemntal data to match our sample coordinates. We also developed a tool called "QueryCube" to access and download data for point coordinates. [Access here]()
  
- Association Analysis: We combine both data types (genomic and environemtnal) by doing association analysis. We apply selected statistical emthods to uncover the relationship between genomics and environments. 

## Data Ingestion 

Use Case 3 mostly uses APIs available via the FAIRiCUBE infrastructure. One data source, that was ingested in the Rasdaman architecture was the [Glocbal Pesticide Grid](https://www.earthdata.nasa.gov/news/new-agricultural-pesticide-use-dataset-nasas-sedac).
## Processing Steps

## Solutions

## Resources

## Partners

Naturhistorisches Museum Wien, Natural History Museum Vienna (NHMW)
