# MISC

<!-- toc -->

## Login without password
```
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub minsu@192.168.20.2
```

## Sort

```
sort -k1 -k2 test.csv
sort -t, -k1,1n -k2,2n test.csv
```

- t 指定分隔符
- k =pos1[,pos2] default is end,

## Make


> 参见 [https://www.zhihu.com/question/36609459](https://www.zhihu.com/question/36609459)

- gcc 编译器，C/ Java/ Fortan等，一个源文件

- make 批处理工具，调用Makefile处理多个源文件

- cmake 跨平台批处理工具，调用CMakeLists.txt自动生成Makefile

- qmake 跨平台批处理工具，处理*.pro

## dpkg

1. 查看已安装软件 dpkg -l | grep ftp
2. 查看安装路径 dpkg -L ftp

## Packaging for R

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
```

## Getting Started

<table>
  <tr>
    <th>Tools</th>
    <th>Function</th>
    <th>Manual</th>
  </tr>
  <tr>
    <td>Gitbook</td>
    <td>Notebook</td>
    <td>https://gitbook.hushuang.me/</td>
  </tr>
  <tr>
    <td>Docker</td>
    <td>CI & CD</td>
    <td>https://www.gitbook.com/book/yeasy/docker_practice/details</td>
  </tr>
  <tr>
    <td>Graphviz</td>
    <td>code flow-chart</td>
    <td>https://graphviz.gitlab.io/_pages/doc/info/lang.html</td>
  </tr>
</table>

