# R

## install

```
tar -zxvf R-3.4.3.tar.gz 
cd R-3.4.3
./configure --with-libpng --with-jpeglib --with-libtiff --with-x --with-blas --with-lapack --enable-R-shlib --enable-R-static-lib --enable-BLAS-shlib && make -j 12 && make install
```

## mirror

加入~/.Rprofile

```
# 设置R交互提示信息
options(prompt="> ")
options(continue="+ ")
# 设置包的本地库（library）路径
.libPaths("C:/my_R_library") 
# 设置CRAN镜像默认地址
local({r <- getOption("repos")
  r["CRAN"] <- "https://mirrors.ustc.edu.cn/CRAN/"
  options(repos=r)
  options(BioC_mirror="http://mirrors.ustc.edu.cn/bioc/")
})
# 启动函数
.First <- function(){
  library(getopt)
  source("http://bioconductor.org/biocLite.R")
  cat("\nWelcome at", date(), "\n")
}
# 会话结束函数
.Last <- function(){
  cat("\nGoodbye at ", date(), "\n")
}
```

## R 打包

```
#创建包的骨架
library(devtools)
create("~/package-name")
setwd("~/package-name")
#添加R包到"~/package-name/R"
#运行测试
load_all()
function_test()
function_test_1()
#生成文档
document()
#打包
build()
#打包测试
check()
# R CMD check --as-cran ~/package-name.tar.gz
```



