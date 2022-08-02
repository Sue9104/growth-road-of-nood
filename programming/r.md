# R

## Install package

> [https://r-coder.com/install-r-packages/](https://r-coder.com/install-r-packages/)

```
install.packages("calendR")
## install from zip source
install.packages("package_path", repos = NULL, type = "source")
## install from R-forge
install.packages("MPAgenomics", repos = "http://R-Forge.R-project.org", dependencies = TRUE)
                 
# install from github
install.packages(devtools)
devtools::install_github("account_name/repository_name")

# install from Bioconduct
install.packages("BiocManager")
BiocManager::install("nanotatoR") 

# install using cmd


```

## Environment

{% code title="~/.Rprofile" %}
```
// Some code# 设置R交互提示信息                                                              
options(prompt="> ")                                                             
options(continue="+ ")                                                           
# 设置包的本地库（library）路径                                                  
#.libPaths("C:/my_R_library")                                                    
# 设置CRAN镜像默认地址                                                           
local({
    r <- getOption("repos")                                                   
    r["CRAN"] <- "https://mirrors.ustc.edu.cn/CRAN/"                                 
    options(repos=r)                                                                 
    options(BioC_mirror="http://mirrors.ustc.edu.cn/bioc/")                          
})                                                                               
# 启动函数                                                                       
.First <- function(){                                                            
    #library(getopt)                                                                 
    #source("http://bioconductor.org/biocLite.R")                                    
    cat("\nWelcome at", date(), "\n")                                                
}                                                                                
# 会话结束函数                                                                   
.Last <- function(){                                                             
    cat("\nGoodbye at ", date(), "\n")                                               
}
```
{% endcode %}

