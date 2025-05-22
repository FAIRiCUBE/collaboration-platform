# How to access and download Copernicus point data with the CDS API

### Reference Use case

Use Case 3

### Problem statement

TIFF files, especially geospatial ones, can be large, slow to process, and often require specialized software or libraries to handle. Downloading them can also be complicated due to their size, hosting requirements, and access restrictions (e.g., login credentials or API limits), making point data a more efficient and accessible alternative in many cases. Working with point data instead of raster formats like TIFFs can be necessary when focusing on specific, localized measurements—such as weather station readings, GPS coordinates, or sampling sites—where high-resolution, full-coverage imagery is unnecessary and overly data-heavy. 

### Envisaged impact

Not being able to easily access point data can hinder work by introducing unnecessary complexity and delays into analysis. Without straightforward access to precise point coordinates, users may be forced to work with larger, more complex datasets (like raster files), which can require more processing power, time, and specialized knowledge to handle. This can slow down the overall workflow, make it more difficult to extract relevant information quickly, and limit the ability to perform real-time analysis or make timely decisions. In fields where speed and precision are critical—such as environmental monitoring, public health, or disaster response—this added complexity can be a significant barrier to effective work.

### Affected component of FAIRiCUBE Hub

FAIRiCUBE Lab (Storage, RAM)

### Proposed solution

Using the Climate Data Store (CDS) Application Program Interface (API). First make sure to set up the CDS API personal access token and isntall the CDS API client. Instructions from Copernicus can be found [here.](https://cds.climate.copernicus.eu/how-to-api)

We provide a script how to get point coordinates [here.](https://github.com/FAIRiCUBE/uc3-drosophola-genetics/blob/main/projects/LandscapeGenomicsPipeline/scripts/getCDSdata.py)

**Additional Requirements:**
- Input coordinates 
- List of variables to retrieve for each coordinate

### Expected benefits

Providing easy access to just the point coordinates from large spatial datasets can have a major impact by simplifying data workflows and making spatial analysis more accessible. It allows users to quickly extract the most relevant information—such as observation locations or sampling points—without dealing with the complexity and size of full raster datasets. This can speed up analyses, reduce storage and processing needs, and enable broader use of geospatial data by users with limited technical resources. Ultimately, it empowers faster decision-making and more targeted insights, especially in resource-limited or time-sensitive scenarios.
