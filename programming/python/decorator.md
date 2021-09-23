# decorator @

> 参考： [http://blog.csdn.net/st831201/article/details/47859275](http://blog.csdn.net/st831201/article/details/47859275)

## 用途

为已经存在的函数或对象添加额外的功能

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

## 特殊用法

### @staticmethod 

不会隐式传入任何变量（self、cls），相当于普通方法，直接访问无需实例化

```python
class XiaoMing:
    @staticmethod
    def say_hello():
        print('同学你好')

XiaoMing.say_hello()
```

### @classmethod 

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

