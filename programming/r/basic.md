# Basic

## Data Structures

| Type       | Dimension                | Function                           |
| ---------- | ------------------------ | ---------------------------------- |
| vector     | 1d data of **same type** | c()                                |
| list       | 1d data of diff type     | list()                             |
| matrix     | 2d data of **same type** | matrix() cbind() rbind()           |
| data.frame | 2d data of diff type     | data.frame(x=1:3,y=c('a','b','c')) |
| array      | Nd data of **same type** | array(1:12,c(2,3,2))               |

`typeof() str()`

`is.character()`，`is.double()`，`is.integer()`，`is.logical()`

`length()  dim() nrow() ncol()`

`attr() attributes()`

`names()`

x\[] <- 0 `#all elements assign 0`

`[`取子列表`, [[`提取某个元素。`x$y`等同于`x[["y"]]`

``



```r
attr(y, "my_attribute") <- "This is a vector"
attr(y, "my_attribute")
str(attributes(y))
```

## Operators

**+  -  \*  /  ^|\*\*  %%  %/%**&#x20;

**<  >  ==  !=  !x  x|y  x\&y  isTRUE(x)**

## Apply

[http://showteeth.tech/posts/15576.html](http://showteeth.tech/posts/15576.html)

| Function | Input            | Output      | Dimension                           |
| -------- | ---------------- | ----------- | ----------------------------------- |
| apply    | list, df, array  | vec, array  | **1表示按行**，**2表示按列**                 |
| lapply   | list, df, vector | list        | 结果长度与input一样                        |
| sapply   |                  | vec, matrix | lapply上设置格式(`simplify`和`USE.NAMES`) |
| vapply   |                  | vec, matrix | sapply上设置行名（FUN.VALUE）              |
| rapply   | list             | list        | lapply递归                            |
| tapply   |                  |             | group by                            |
| mapply   | vector不限个数       | vec, matrix |                                     |
| eapply   | environment      | list        |                                     |



```
# apply
x<-matrix(1:12,ncol=3)
apply(x,1,sum)

# lapply
# default data.frame is processed by columns
x <- cbind(x1=3, x2=c(2:1,4:5))
lapply(data.frame(x), sum) 
## $x1
## [1] 12
## $x2
## [1] 12
sapply(data.frame(x), sum) 
##x1 x2 
##12 12



# mapply
mapply(max,x,y,z)


# tapply
# tapply(X, INDEX, FUN = NULL)
# mean of iris$Petal.Length group by species
tapply(iris$Petal.Length,iris$Species,mean)

```

## Dplyr

{% embed url="https://dplyr.tidyverse.org/articles/dplyr.html" %}

```
x %>% f(y) turns into f(x, y)
```

Rows: [filter()](https://dplyr.tidyverse.org/reference/filter.html) [slice()](https://dplyr.tidyverse.org/reference/slice.html) [arrange()](https://dplyr.tidyverse.org/reference/arrange.html)

Columns: [select()](https://dplyr.tidyverse.org/reference/select.html) [rename()](https://dplyr.tidyverse.org/reference/rename.html) [mutate()](https://dplyr.tidyverse.org/reference/mutate.html) [relocate()](https://dplyr.tidyverse.org/reference/relocate.html)

Groups of row: [summarise()](https://dplyr.tidyverse.org/reference/summarise.html)&#x20;

## Command Line

1. docopt
2. argparser
