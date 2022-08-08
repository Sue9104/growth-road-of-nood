# MISC

## Basic

### Memory

ps命令

* VSZ：程序被分配的内存
* RSS：程序实际占用内存（不含交换区）

htop命令

* VIRT：程序被分配的内存
* RES：程序实际占用内存（不含交换区）
* SHR：共享内存
* Mem颜色：green\(used\)、blue\(buffer\)、yellow\(cached\)

## Terminal color scheme

[Gogh](https://mayccoll.github.io/Gogh/#0) : Frontend Galaxy

Set this colorscheme to default, and change the highlight color.

## Login without password

```text
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub minsu@192.168.20.2
```

## Sort

```text
sort -k1 -k2 test.csv
sort -t, -k1,1n -k2,2n test.csv
```

* t 指定分隔符
* k =pos1\[,pos2\] default is end,

## Make

> 参见 [https://www.zhihu.com/question/36609459](https://www.zhihu.com/question/36609459)

* gcc 编译器，C/ Java/ Fortan等，一个源文件
* make 批处理工具，调用Makefile处理多个源文件
* cmake 跨平台批处理工具，调用CMakeLists.txt自动生成Makefile
* qmake 跨平台批处理工具，处理\*.pro

## dpkg

1. 查看已安装软件 dpkg -l \| grep ftp
2. 查看安装路径 dpkg -L ftp

## Packaging for R

```text
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

## Tools

| Tools | Function | Manual |
| :--- | :--- | :--- |
| Gitbook | Notebook | https://gitbook.hushuang.me/ |
| Docker | CI & CD | https://www.gitbook.com/book/yeasy/docker\_practice/details |
| Graphviz | code flow-chart | https://graphviz.gitlab.io/\_pages/doc/info/lang.html |
| Edrawmax | flow-chart | https://www.edrawsoft.com/en/download-edrawmax.html |
| Navicat | database relation | https://www.navicat.com.cn/ |



