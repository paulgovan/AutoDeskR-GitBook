
# Introduction
AutoDeskR {{ "AutoDeskR" | cite }} is an R package that provides an interface to the:
* Authentication API for obtaining authentication to the AutoDesk Forge Platfrom.
* Data Management API for managing data across the platform's cloud services. 
* Design Automation API for performing automated tasks on model files in the cloud.
* Model Derivative API for translating design files into different formats, sending them to the viewer app, and extracting model data.
* Viewer for rendering 2D and 3D models.

See [developer.autodesk.com](https://developer.autodesk.com) for more information.

## Motivation


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

