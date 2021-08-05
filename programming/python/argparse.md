# argparse

## 建立解析器

```python
import argparse
parser = argparse.ArgumentParser(
  description=’This is a PyMOTW sample program’,
)
```

## 生成选项

```python
group.add_argument('-i', '--input', type=str,          
    dest='dataFN', metavar='fileName', 
    action="store", default=None,     
    help='specify input file in one of the following formats:\n'  
)
```

参数解析：

* dest: 存储变量名
* metavar: 变量解释
* nargs: 变量个数， \* 以列表形式保存
* required: 是不是必填项，True/False
* action: store\_true 表示选项不需要接收参数（True）；append 将同一个参数的值加入列表；count 计算关键词出现次数

### 添加互斥选项

```python
group = parser.add_mutually_exclusive_group()
```

### 添加group

```python
group = parser.add_argument_group('trees', groupDescription)
```

## 打印

```python
parser.parse_args()
```

