# Basic

## Data Structure

### 序列类型

| Type  | Symbol           | Content                           |
| ----- | ---------------- | --------------------------------- |
| List  | \[1，2]           | 可变序列                              |
| Tuple | 1,2  \|\|  (1，2) | 不可变的                              |
| Set   | set()            | 不重复元素组成的无序容器，可进行数学运算（- \| & ^），{} |
| Dict  | {} \|\| dict()   | 键值对                               |

### 容器数据类型 Container Datatypes

> 参考 [collections](https://docs.python.org/3/library/collections.html#collections.deque)

namedtuple  deque  ChainMap  Counter  OrderedDict  defaultdict  UserDict  UserList UserString

### 抽象基类 Abstract Base Class

> 参考：collections.abc&#x20;

Container  Hashable  Iterable  Iterator  Collection Sequence

## Function

### typing 类型标注

|                                                    |                                    |
| -------------------------------------------------- | ---------------------------------- |
| List, Turple, Sequence                             | 数组类型                               |
| NewType(key, valuetype)                            | 自定义新类型                             |
| TypeVar, Generic                                   | TypeVar定义，Generic泛型类型              |
| Any                                                | 混用动态和静态类型                          |
| Sized, Iterable, Iterator,Callable                 | 名义性子类型                             |
| Dict, DefaultDict, OrderedDict                     | 字典                                 |
| Generator\[YieldType, SendType, ReturnType]        |                                    |
| Text                                               | str别名，对python2向下兼容                 |
| IO, TextIO, BInaryIO                               | IO类型                               |
| Pattern, Match                                     | re.compile, re.match返回类型           |
| NamedTuple, TypedDict                              |                                    |
| Optional                                           | `Optional[X]` 等价于 `Union[X, None]` |
| Literal                                            | 函数参数的值等价于提供的字面量（或者几个字面量的其中之一）      |
| overload, final, no\__typecheck, runtime_checkable | 装饰器                                |

## Class

### \_\_new\_\_ vs \_\_init\_\_

* _\_\_new\_\_:_ 创建实例，第一个参数是cls
* _\_\_init\_\_:_ 实例初始化，第一个参数是self

### Attribute

* **Class Attribute will effect every instance(@property).**
* **Instance Attribute only works in current object(\_\_int\_\_).**

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



## Decorator

* 为已经存在的函数或对象添加额外的功能
* 不确定的执行顺序

```python
# 基于函数的装饰器
def logging(level):
    def wrapper(func):
        def inner_wrapper(*args, **kwargs):
            print("[{level}]: enter function {func}".format(
                level = level, func = func.__name__
            ))
            return func(*args, **kwargs)
        return inner_wrapper
    return wrapper
@logging(level='INFO')
def say(something):
    print("say {}!".format(something))


# 基于类的装饰器
## input: callable 对象
## output: callable 对象
class logging(object):
    def __init__(self, level="INFO"):
        self.level = level
    def __call__(self, func):
        def wrapper(*args, **kwargs):
            print("[{level}]: enter function {func}".format(
                level = level, func = func.__name__
            ))
            func(*args, **kwargs)
        retrun wrapper
@logging(level='INFO')
def say(something):
    print("say {}!".format(something))        
```

### @staticmethod&#x20;

不会隐式传入任何变量（self、cls），相当于普通方法，直接访问无需实例化

```python
class XiaoMing:
    @staticmethod
    def say_hello():
        print('同学你好')

XiaoMing.say_hello()
```

### @classmethod&#x20;

将class作为第一个变量，常用来产生object。直接访问无需实例化

```python
class Mytask:
    @classmethod
    def classmeth(cls, args):
        # will generate object
        return cls(args=args)
    @staticmethod
    def staticmeth(*args):
        return args
    def normalmeth(*args):
        return args
```

### @property

参数检查，将方法作为参数使用

```python
class Student(object):

  @property
  def score(self):
      return self._score

  @score.setter
  def score(self, value):
      if not isinstance(value, int):
          raise ValueError('score must be an integer!')
      if value < 0 or value > 100:
          raise ValueError('score must between 0 ~ 100!')
      self._score = value
```

## Mixin

* 功能单一，按需继承
* 本身不能实例化，仅可被子类继承

```python
class ReprMixin:
  def __repr__(self):
    s = self.__class__.__name__ + '('
      for k, v in self.__dict__.items():
        if not k.startswith('_'):
          s += '{}={}, '.format(k, v)
    s = s.rstrip(', ') + ')'  # 将最后一个逗号和空格换成括号
    return s
    
class Person(ReprMixin):
    def __init__(self, name, gender, age):
        self.name = name
        self.gender = gender
        self.age = age

p = Person("小陈", "男", 18)
print(p)  # Person(name=小陈, gender=男, age=18)
```
