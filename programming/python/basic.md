# Basic

## Data Structure

### 序列类型

| Type | Symbol | Content |
| :--- | :--- | :--- |
| List | \[1，2\] | 可变序列 |
| Tuple | 1,2  \|\|  \(1，2\) | 不可变的 |
| Set | set\(\) | 不重复元素组成的无序容器，可进行数学运算（- \| & ^），{} |
| Dict | {} \|\| dict\(\) | 键值对 |

### 容器数据类型 Container Datatypes

> 参考 [collections](https://docs.python.org/3/library/collections.html#collections.deque)

namedtuple  deque  ChainMap  Counter  OrderedDict  defaultdict  UserDict  UserList UserString

### 抽象基类 Abstract Base Class

> 参考：collections.abc

Container  Hashable  Iterable  Iterator  Collection Sequence

## Class

### \_\_new\_\_ vs \_\_init\_\_

* _\_\_new\_\_:_ 创建实例，第一个参数是cls
* _\_\_init\_\_:_ 实例初始化，第一个参数是self

### Attribute

* **Class Attribute will effect every instance\(@property\).**
* **Instance Attribute only works in current object\(\_\_int\_\_\).**

```python
class Employee: 
    
    # class attribute
    value = 0 
    @property
    def count(self):
        print('Getting value') 
        return self._value
    @value.setter 
    def value(self, value): 
        print('Setting value to ' + value) 
        self._value = value       
    @value.deleter 
    def value(self): 
        print('Deleting value') 
        del self._value 
    
    # instance attribute
    def __init__(self, value): 
        self._value = value     
```

### metaclass

* 动态创建类

```python
type(class_name, bases, attr_dict)
```

* metaclass: 创建class object的class

```python
class UpperAttrMetaclass(type):
    def __new__(cls, cls_name, bases, attr_dict):
        uppercase_attr = {}
        for name, val in attr_dict.items():
            if name.startswith('__'):
                uppercase_attr[name] = val
            else:
                uppercase_attr[name.upper()] = val
        return super(UpperAttrMetaclass, cls).__new__(cls, cls_name, bases, uppercase_attr)
```

* 主要应用场景：创建API，如Django的ORM

```python
class Person(models.Model):
    name = models.CharField(max_length=30)
    age = models.IntegerField()
```





