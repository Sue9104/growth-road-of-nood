# Package

## Devtools

{% embed url="https://devtools.r-lib.org/" %}

![](<../../.gitbook/assets/2022-08-09 19-33-30 的屏幕截图.png>)

![](<../../.gitbook/assets/2022-08-09 19-36-36 的屏幕截图.png>)

### Quick Start

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

