# Templates for DynACof input files

## Introduction
This repository contains the templates for the input parameter files needed for a [DynACof](https://vezy.github.io/DynACof/) simulation, and was made to simplify the user experience

## Download

### Non-coders
If you don't have a GIT client installed, or if you don't even know what GIT is, you can download all the template files at once using this [link](https://github.com/VEZY/DynACof_inputs/archive/master.zip).

### Experienced users
To clone the repository, use this command:
```
git clone https://github.com/VEZY/DynACof_inputs.git
```
## Details
The values of the parameters in these files can be customized to fit new conditions. To do so, you'll have to download this repository, to open the files and identify the parameters you need to adapt, and to use these new input files for your simulation.

## Example

Here is an example call to DynACof using custom parameter files:
``` r
# Install the package if not already present in your library:
# install.packages("remotes")
# remotes::install_github("VEZY/DynACof")

# Load the package
library(DynACof)

# Execute the model using your custom parameter files, located for the example in
# the folder "1-Input":
DynACof(Inpath = "1-Input/",
        FileName = list(Site = "Site.R", Meteo ="Meteorology.txt",
                        Soil = "Soil.R",Coffee = "Coffee.R",
                        Tree = "Tree.R"))
```
