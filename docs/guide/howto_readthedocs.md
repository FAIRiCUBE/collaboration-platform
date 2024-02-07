# How to provide input/content to this FAIRiCUBE-HUB Community collaboration platform

The content of this collaboration platform is managed via a github repository, which is connected to [ReadTheDocs](https://about.readthedocs.com) resulting in automatically deployments of newly merged contents to its final destination: the [FAIRiCUBE-HUB - Getting started, Examples & How To's](https://fairicube.readthedocs.io/en/latest/)

All documents are provided as Markdown-files (i.e. *.md).
Help with the Markdown-syntax can be found [here](https://daringfireball.net/projects/markdown/syntax)


## First, clone this repository to your local computer:

e.g from the command-line:

    $> git clone git@github.com:FAIRiCUBE/collaboration-platform.git

or by using any other of the other methods offered by github.


## Building the docs (for local usage/evaluation)

    $> conda install -c conda-forge mkdocs mkapi
or

    $> pip3 install mkdocs mkapi

Thereafter, you can build a local version of the documentation by:

    $> cd  <to the directory containing the 'mkdocs.yml' file>

then run:

    $> mkdocs serve -a localhost:8001

this will provide a local web-server offering the newly build documentation at the following location: **http://localhost:8001/**

This allows it to easily check locally for all the formatting , structuring, etc. before uploading it to the repository.


## Start providing/editing documents

Before you begin, please make sure that you **start a new branch** for your additions/editing.

    $> git checkout -b  <new_feature_name>
<br>
*Note: The Structure of the collaboration site (provided on the left side) is defined in the* _**mkdocs.yml**_ *file.*<br>
*Changes to this structure are not immediately viewable under **http://localhost:8001/**.* <br>
*In order to see you changes there, you need to restart the local web-server ('mkdocs serve -a localhost:8001').*<br>
*All other changes to the documents are immediately rendered locally.*

Now you can start creating your content or edit already existing information.

Once you finished all your edits or newly created documents and have thoroughly checked them in the local instance, you can submit your input to the git repository to be merged into the main branch.


<br>

##### Some rules we ask you to follow:

* Please try to keep the structure as much as possible. Try not to introduce unnecessary directories.
* xx








