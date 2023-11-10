# FAIRICUBE Hub

### Introduction

The FAIRiCUBE Hub provides a complete working environment where users can access algorithms and data remotely to obtain computing resources and tools that they might not otherwise have and avoid the need to download and manage large volumes of data. This new approach removes the need to transfer/download large e.g. Earth Observation data sets around the world, while increasing the analytical power available research scientists, industry, operational service providers, regional authorities, and policy analysts.

The FAIRiCUBE Hub is based on the existing software named EOxHub, which is extended in two ways to provide the FAIRiCUBE *Collaborative Development Tools*:

* Extended support for teams as part of the multi-user plan. Allow for easier sharing of versioned notebooks and other artifacts within the team but not necessarily the public.
* Integrated support for Machine Learning (ML) workflows. This includes the versioning, sharing, and collaborative using of all ML artifacts like code, data, models, results, etc. Based on user feedback, the readily available Open-Source tools like Data Version Control (DVC), MLflow, Kubeflow, or similar, will be integrated during the project.

The FAIRiCUBE Hub manages use cases and their users. The Hub provides for each use case a workspace or tenant,
assigns project resources, hosts project artifacts, provides a shared storage for result dissemination, and integrates team collaboration tools. It also controls visibility of results of individual user projects so that they can be made part of a FAIRiCUBE public portrayal.

A FAIRiCUBE user project comprises numerous own applications, interfaces, services, and data available in the provided workspace.

### Overview

* **[FAIRiCUBE Catalog](fic_catalog.md):** The integrated catalog providing metadata and references to ingested datasets, processes, and models available from FAIRiCUBE.
* **FAIRiCUBE Hub:** The overall FAIRiCUBE technical environment encompassing the FAIRiCUBE Catalog, FAIRiCUBE Services and Applications, as well as the FAIRiCUBE Lab.
* **FAIRiCUBE Workspace:** The user area within the FAIRiCUBE Lab where users are able to collaborate and share the content of their workspaces.
* **[FAIRiCUBE Lab](jupyterlab.md):** A single container for all workspaces providing the interface to back-ends via various back-end protocols as well as an execution environment for user provided workloads.
* **FAIRiCUBE Services/Apps:** Components providing various ways to access the data and processing facilities provided by FAIRiCUBE.
* **[FAIRiCUBE Knowledge Base](knowledgebase.md):** Provides a set of tools to enable appropriate knowledge of how to apply algorithms and ML techniques to solve similar demands.


<p align="center">
    <img src="../../images/fairicube_architecture.gif" alt="FAIRiCUBE Architectur.gif" />
</p>
The figure shown above provides an Overview of the overall FAIRiCUBE Architecture.


### Envisioned Data-Flow  in FAIRiCUBE

<p align="center">
    <img src="../../images/FAIRiPATH_data_flow.png" alt="FAIRiPATH_data_flow.png" />
</p>

In the figure above an overview showing the flow of data and metadata within the FARiCUBE Hub system is given. Data provided will be submitted vi STAC-API to the STAC catalog holding the metadata. If required some pre-processing steps  (e.g. conversions, geographic transformations and if necessary some gap-filling procedures) might be applied to the respective dataset. Such pre-processing steps are especially useful to harmonize datasets (e.g. their resolution, projection, etc.) prior to ingestion.
Once pre-processing is finished data will be ingested into the data-store from where is will be readily available to further actions applied by the user. These include further data analysis, visualization and ML-Training. All results can be submitted into the storage for further usage or fed into ML-Models.


