# Templates for DynACof input files

## Introduction
This repository contains the templates for the input parameter files needed for a [DynACof](https://vezy.github.io/DynACof/) simulation (R-version), and was made to simplify the user experience.

## Download

### Non-coders
If you don't have a GIT client installed, or if you don't even know what GIT is, you can download all the template files at once using this [link](https://github.com/VEZY/DynACof_inputs/archive/master.zip).

### Experienced users
To clone the repository, use this command:
```
git clone https://github.com/VEZY/DynACof_inputs.git
```
## Details
The values of the parameters in these files can be customized to fit new conditions. To do so, you'll have to download this repository, open the files, identify the parameters you need to adapt, and use these new input files for your simulation.

## Example

All steps are made using R for simplicity in this example.

1. The first step is to download (or clone) this repository to get the data. For this example, we will download the repository into a temporary directory created from R.

    * If you have `GIT` installed on your computer:
```r
# install.packages("git2r")
dynacof_data= normalizePath(tempdir(), winslash = "/", mustWork = FALSE)
git2r::clone("https://github.com/VEZY/DynACof_inputs.git",dynacof_data)
```

    * or else, downloading the `ZIP` archive:
```r
dynacof_data= normalizePath(tempdir(), winslash = "/", mustWork = FALSE)
data_dir_zip= normalizePath(file.path(dynacof_data,"master.zip"), winslash = "/", mustWork = FALSE)
download.file("https://github.com/VEZY/DynACof_inputs/archive/master.zip", data_dir_zip)
unzip(data_dir_zip, exdir = dynacof_data)
unlink(data_dir_zip)
dynacof_data= normalizePath(list.dirs(dynacof_data)[2])
```

1. Then you have to download the DynACof package. To do so, you have to install the `remotes` package (or `devtools`):

    * For `remotes`:
    ``` r
    install.packages("remotes")
    remotes::install_github("VEZY/DynACof")
    ```

    * For `devtools`:
    ``` r
    install.packages("remotes")
    remotes::install_github("VEZY/DynACof")
    ```

    The `remotes` package is lighter than `devtools`. But if you already are an R developer you should have `devtools` installed on your system.

1. Then, load the `DynACof` package:
``` r
library(DynACof)
```

1. And finally, execute the model using your custom parameter files:
``` r
sim= DynACof(Inpath = dynacof_data,
                FileName = list(Site = "site.R", Meteo ="meteorology.txt",
                                Soil = "soil.R",Coffee = "coffee.R",
                                Tree = "tree.R"))
```

And DynACof should run the simulation.

## Julia version
If you need to run a simulation with the Julia version of DynACof from R, you have to use a different repository with the Julia input format. This repository is in [DynACof.jl_inputs](https://github.com/VEZY/DynACof.jl_inputs).
