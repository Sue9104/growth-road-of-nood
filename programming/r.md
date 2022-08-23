# R

## **数据结构**

<figure><img src="../.gitbook/assets/Aiomic vector （原子肉量）.png" alt=""><figcaption></figcaption></figure>

更多：[https://bookdown.org/xiao/RAnalysisBook/section-2.html](https://bookdown.org/xiao/RAnalysisBook/section-2.html)

[https://haoeric.gitbooks.io/r-advanced/content/datastructure.html](https://haoeric.gitbooks.io/r-advanced/content/datastructure.html)****

**特殊值**

| 类型   | 含义                   |
| ---- | -------------------- |
| NA   | 缺失值(not available )  |
| NaN  | 无意义的值(not a number ) |
| NULL | 空数据                  |
| Inf  | <p></p><p>无穷大</p>    |

## **Bioconductor**

**Softwares**

Bioconductor Home - Softwares - Biological Question

* browseVignettes("DESeq2") 查看教程
* NEWS 版本更新记录

**Workflows**

经典的分析流程

Bioconductor Home - Common Work Flows



## 常用命令

| help(function, package=‘library’) \| ? | <p><br>查看帮助</p>   |
| -------------------------------------- | ----------------- |
| example(‘function’)                    | 用法举例              |
| help.search(function) \| ??            | 无法确定function所在的包  |
| apropos(‘test’)                        | 无法确定具体的function名  |
| vignette(‘function’)                   | 文档                |
| RSiteSearch()                          | <p>搜索相关资源<br></p> |

工作空间

| options()                       | 显示或设置当前的选项                      |
| ------------------------------- | ------------------------------- |
| getwd()                         | 显示当前的目录                         |
| setwd()                         | 修改工作目录                          |
| ls()                            | 列出当前工作空间中的对象                    |
| rm()                            | 删除一个或多个对象                       |
| history()                       | 最近使用过的命令                        |
| savehistory("myfile")           | 保存命令历史到文件myfile中（默认值为.Rhistory） |
| save.image("myfile")            | 保存工作空间到文件myfile中（默认值为.RData）    |
| save(objectilist,file="myfile") | 保存指定对象到一个文件中                    |
| load("myfile")                  | 读取一个工作空间到当前会话中                  |
| source("filename")              | 执行一个脚本(.R)                      |
| sink("filename")                | 将文本输出重定向到文件filename             |
| q()                             | 退出                              |

\


工具包

| install.packages()    | <p><br></p> |
| --------------------- | ----------- |
| detach(“packages:\*”) | 移除包         |
| remove.packages("\*") | 卸载包         |
| search()              | 显示已加载的包的列表  |

\




数据类型

\


更多：

[https://bookdown.org/xiao/RAnalysisBook/section-2.html](https://bookdown.org/xiao/RAnalysisBook/section-2.html)

[https://haoeric.gitbooks.io/r-advanced/content/datastructure.html](https://haoeric.gitbooks.io/r-advanced/content/datastructure.html)

\


\


特殊值

| NA   | 缺失值(not available )  |
| ---- | -------------------- |
| NaN  | 无意义的值(not a number ) |
| NULL | 空数据                  |
| Inf  | 无穷大                  |

\


编程风格

[https://google.github.io/styleguide/Rguide.html](https://google.github.io/styleguide/Rguide.html)

\


更多教程

[https://rstudio.github.io/r-manuals](https://rstudio.github.io/r-manuals)

http://manuals.bioinformatics.ucr.edu/home/programming-in-r

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

## 编程风格

[https://google.github.io/styleguide/Rguide.html](https://google.github.io/styleguide/Rguide.html)\


## 更多教程

[https://rstudio.github.io/r-manuals](https://rstudio.github.io/r-manuals)

http://manuals.bioinformatics.ucr.edu/home/programming-in-r
