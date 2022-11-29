# Package

## Installation

> [https://cran.r-project.org/doc/manuals/r-patched/R-admin.html#Installing-packages](https://cran.r-project.org/doc/manuals/r-patched/R-admin.html#Installing-packages)
>
> [https://www.bioconductor.org/install/#install-bioconductor-packages](https://www.bioconductor.org/install/#install-bioconductor-packages)

### repos

```
r <- getOption("repos")
getOption("repos")                                                        
r["CRAN"] <- "https://mirrors.ustc.edu.cn/CRAN/"                               
options(repos=r)                                                               
options(BioC_mirror="http://mirrors.ustc.edu.cn/bioc/") 
```

### available packages

```
# CRAN
av <- available.packages(filters=list())
av[av[, "Package"] == pkg, c("Depends", "OS_type")]


# bioconductor
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install() # install latest bioc
source("https://bioconductor.org/biocLite.R") # R<3.5
BiocInstaller::biocLite(c("GenomicFeatures")) # R<3.5

## check available
BiocManager::valid("*ggplot*") 

## test that the installed packages

# Updating packages

```

### Install packages

```
# install specific packages
R CMD INSTALL -l /path/to/library pkg1 pk2
install.packages(c("Rcmdr"), dependencies = TRUE)
BiocManager::install(c("ggplot2")) 
remotes::install_github()

# check installed packages
## CRAN
inst <- packageStatus()$inst
inst[inst$Status != "ok", c("Package", "Version", "Status")]
## Bioconductor
BiocManager::valid()
BiocManager::valid()$too_new
BiocManager::valid()$out_of_date

# updating
BiocManager::install()
```

### installed path

```
# installed path: R_HOME/library、 R_HOME/site-library、R_HOME/etc/Rprofile.site
# installed path VAR: R_LIBS_USER and R_LIBS_SITE
.libPaths()


# library: R_LD_LIBRARY_PATH, R_JAVA_LD_LIBRARY_PATH and LD_LIBRARY_PATH
## export R_LD_LIBRARY_PATH="`R RHOME`/lib:/opt/local/lib"
```

## Devtools

{% embed url="https://devtools.r-lib.org/" %}

![](<../../.gitbook/assets/2022-08-09 19-33-30 的屏幕截图.png>)

![](<../../.gitbook/assets/2022-08-09 19-36-36 的屏幕截图.png>)

### Quick Start

{% embed url="https://r-pkgs.org/" %}

```
// init
library(devtools)
create("~/package-name")
setwd("~/package-name")
use_git()
use_mit_license()

// create R script file
use_r("filename")
// change filename both in R and tests
rename_files("strsplit1", "str_split_one")

// enter package environment
load_all()
function_test()

// test, wrinting to tests folder
use_testthat()
use_test("function")

// requirements, writing to DESCRIPTION
use_package("stringr")

// document, writing to NAMESPACE and rd files
document()
use_readme_rmd()
build_readme()

// final
check()
install()

// 打包
```

### File Format

| file       | content              | function        |
| ---------- | -------------------- | --------------- |
| rds        | single R object      | saveRDS、readRDS |
| RData(rda) | multile R object     | save、load       |
| rd         | roxygen comment file |                 |

### Data

#### internal data

R/sysdata.rda

x <- [sample](https://rdrr.io/r/base/sample.html)(1000) usethis::[use\_data](https://usethis.r-lib.org/reference/use\_data.html)(x, mtcars, internal = TRUE)

#### Raw Data

put the original files in `inst/extdata`

[system.file](https://rdrr.io/r/base/system.file.html)("extdata", "iris.csv", package = "readr", mustWork = TRUE)

#### Export Data

files in data/ is default exported





## Roxygen2

{% embed url="https://cran.r-project.org/web/packages/roxygen2/vignettes/" %}

### Reuse

`@describeIn <destination> <description>`&#x20;

```
#' Power
#' @param x base
#' @param exp exponent
power <- function(x, exp) x ^ exp

#' @describeIn power Square a number
square <- function(x) power(x, 2)

#' @describeIn power Cube a number
cube <- function(x) power(x, 3)
```

`@inheritParams <source function>`

`@inheritParams <source function> <params`, `return`, `title`, `description`, `details`, `seealso`, `sections`, `references`, `examples`, `author`, `source`, `note>`

@`inheritSection <pkg::source function> <section title>`

``

