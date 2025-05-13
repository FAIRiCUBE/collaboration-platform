# UC3 - Drosophila Genetics

Combining earth observation and genomics data to study the evolutionary history of the fruit fly Drosophila melanogaster.

In our “Drosophila genomics” use case, we take advantage of comprehensive earth observation data for climate and land use available in the public domain. We will combine environmental data with genomic information of fruit fly DNA samples from more than 300 European Drosophila melanogaster populations that were densely sampled through time and space by [DrosEU](https://droseu.net), our partner consortium. We are developing tools that facilitate extracting information for sample coordinates from gridded datasets to identify links between genetic variation along the whole Drosophila melanogaster genome and environmental variation.

This approach will allow to identify genes that are putatively under selection and involved in adaptation to environmental change. Using machine learning approaches, we further aim to identify combinations of environmental factors that may influence the genetic diversity in natural populations which will help us to better understand the impact of climate change on the accelerating biodiversity crisis.

## Research Questions

1. How does environmental variation across space and time correlate with patterns of genetic diversity in Drosophila melanogaster populations?
2. Which genomic regions or genes in Drosophila melanogaster show signatures of adaptation to specific environmental conditions?
3. Can combinations of environmental factors predict changes in genetic structure or the presence of adaptive alleles in natural populations?

## Workflow

We work with genomic data from Drosophila melanogaster at population level, available at [DEST.bio](https://dest.bio/). This genomic data is availbale at a common data format called "Variant Cal Format" or short VCF. From these VCF files, we generate so-called Allele Frequencies for each population.
Environmental data is available from various sources, matching our regions and times of interest. We used FAIRiCUBE infrastructure to access earth observation and environemntal data to match our sample coordinates. We also developed a tool called [QueryCube](https://querycube.nilu.no/) to access and download data for point coordinates.
We combine both data types (genomic and environemtnal) by doing association analysis. We apply selected statistical emthods to uncover the relationship between genomics and environments. 

The complete workflow including code and instructions can be found in the GitHub Repository of [UseCase3](https://github.com/FAIRiCUBE/uc3-drosophola-genetics/tree/main/projects/LandscapeGenomicsPipeline).

## Data and ingestion 

Use Case 3 mostly uses APIs available via the FAIRiCUBE infrastructure. One data source, that was ingested in the Rasdaman architecture was the [Glocbal Pesticide Grid](https://www.earthdata.nasa.gov/news/new-agricultural-pesticide-use-dataset-nasas-sedac).

### Environmental And Genomic Data Filtering

To ensure high-quality and interpretable analyses, the environmental dataset underwent a thorough filtering process. The following criteria were used to clean and retain only informative and reliable data points:

#### Removal of Records with Missing Coordinates
Sample entries lacking geographic coordinates (latitude and/or longitude) were excluded, as spatial location is essential for linking environmental variables with genetic data. These records cannot be reliably used in spatial or genotype-environment association analyses.

#### Removal of Records with Missing Time Information

Observations without a valid timestamp (e.g., year, season, or date) were filtered out. Temporal information is critical for aligning genetic sampling with environmental conditions and for detecting temporal trends.

#### Filtering Out Missing Environmental Values

Any data points with missing values for one or more environmental variables were removed. Incomplete records can bias statistical models and reduce interpretability, so only complete cases were retained for analysis.

#### Exclusion of Monomorphic Environmental Variables

Environmental variables showing no variation (i.e., constant across all samples) were discarded. Such variables do not contribute to explaining genetic variation and can interfere with statistical modeling.

## Processing steps and ML applications

### Converting VCF File to Allele Frequency File
Raw variant data in VCF (Variant Call Format) is processed to extract allele frequency information per population or individual. This step transforms the VCF into a tabular format suitable for downstream statistical analysis.

### Annotating SNPs
Single Nucleotide Polymorphisms (SNPs) are annotated using reference databases to determine their genomic context (e.g., intergenic, intronic, exonic) and potential functional impacts. This aids interpretation and prioritization of variants.

#### Performing Linear Regression
Linear regression is used to test for associations between allele frequencies (or genotypes) and continuous environmental or phenotypic variables. This identifies candidate loci under selection or related to traits of interest.

### Performing LFMM (Latent Factor Mixed Models)
LFMM accounts for unobserved confounding factors such as population structure by integrating latent factors into a mixed model framework. This method enhances the detection of true genotype-environment associations while controlling for false positives.

### Performing RDA (Redundancy Analysis)
RDA is a multivariate statistical method that examines how much of the genetic variation can be explained by environmental predictors. It is particularly useful for identifying patterns of local adaptation and visualizing genotype-environment relationships.

## Solution(s) 

dd


## Resources

### Environmental Data

We used FAIRiCUBE infrastructure to access earth observation and environmental data from the following sources:

### Genomic Data

- DEST Data
   - https://dest.bio/
- Vienna City Fly
  - https://nhmvienna.github.io/ViennaCityFly/
 

### Programs and Software
- Python
   - https://www.python.org/
- R
   - https://www.r-project.org/
- VCFTools
  - http://vcftools.github.io/license.html

## Partners

Naturhistorisches Museum Wien, Natural History Museum Vienna (NHMW)
