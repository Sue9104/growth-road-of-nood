# 模块查看

## 查看已安装的包

- ```perldoc perllocal``` 

- ```perl -V``` 　＠INC路径
 + /lib perl 内置的
 + /site/lib 后来自己安装的
 
- ``` find  `perl -e 'print "@INC"'` -name '*.pm'  ```
 
- ```perldoc -l IO::All```

## 查看帮助文档

```
perldoc IO::All
```

## 查看源代码

```
perldoc -m IO::All
```
