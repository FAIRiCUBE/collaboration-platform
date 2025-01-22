# How to download genomic data from Drosophila via Jupyter Notebook

## Reference Use case

Use Case 3

## Problem statement

When attempting to download genomic data from a custom resource, the size of the dataset somethimes leads to termination if the downloading process. Uploading again to a HUB can be delayed as well.

## Envisaged impact

Large genomic datasets, particularly from complex organisms such as Drosophila melanogaster, often result in long up- and download times, which can be exacerbated by unstable network connections or server limitations. This slow data retrieval can impede the progress of research, leading to inefficiencies and delays. Moreover, large data files often require special handling and storage capabilities, further complicating the process. 

## Affected component of FAIRiCUBE Hub

FAIRiCUBE Lab (Storage, CPU, RAM and Network) 

## Proposed solution

Direct download via wget in a Jupyter Notebook. 

[https://github.com/FAIRiCUBE/uc3-drosophola-genetics/blob/main/projects/Notebooks/HUB/GetGenomicData.ipynb](https://github.com/FAIRiCUBE/uc3-drosophola-genetics/blob/main/projects/Notebooks/HUB/GetGenomicData.ipynb)

## Expected benefits

Setting tries=Inf in the ensures uninterrupted data downloads by automatically retrying in case of network issues. This improves download reliability, reduces the risk of incomplete data, and saves time by eliminating the need for manual restarts, allowing researchers to focus on analysis instead of troubleshooting.
