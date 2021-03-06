
# Introduction
AutoDeskR {{ "AutoDeskR" | cite }} is an R package that provides an interface to the:
* Authentication API for obtaining authentication to the AutoDesk Forge Platform.
* Data Management API for managing data across the platform's cloud services. 
* Design Automation API for performing automated tasks on model files in the cloud.
* Model Derivative API for translating design files into different formats, sending them to the viewer app, and extracting model data.
* Viewer for rendering 2D and 3D models.

See [developer.autodesk.com](https://developer.autodesk.com) for more information.

## Motivation
The AutoDesk Forge Platform is an excellent set of cloud services, APIs, and resources for developers to create data-centric design apps. R has quickly become the most popular programming language for data analysis, and, in fact, one of the most popular programming languages overall ([link](http://spectrum.ieee.org/computing/software/the-2015-top-ten-programming-languages)). The motivation for AutoDeskR was to bring the functionality of the AutoDesk Platform together with R's powerful data management capabilities. Now users can view 3D models, manage design data, convert design files into different formats, automate design processes, all from within R. 

## Getting Started {#getting-started}

To install AutoDeskR in [R](https://www.r-project.org):

```
install.packages("AutoDeskR")
```

To install the development version:

```
devtools::install_github('paulgovan/autodeskr')
```

Then load the package:

```
library(AutoDeskR)
```

