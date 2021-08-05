# decorator @

> 参考： [http://blog.csdn.net/st831201/article/details/47859275](http://blog.csdn.net/st831201/article/details/47859275)

## 用途

在目的函数执行前，执行一些自己的操作

```python
def a(fn):  
    print 'a'  

    def d(st):  
        print st+'d'  
    return d  

def b(fn):  
    print 'b'  
    return fn  

@a  
@b  
def c(st):  
    print st  

c('c')
```

## 特殊用法

* @staticmethod 不会隐式传入任何变量
* @classmethod 将class作为第一个变量
* @property 参数检查

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

