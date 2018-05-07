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