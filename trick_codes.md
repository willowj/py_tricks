### Autovivification 自实现

- >  dict to tree    # or inherit  defaultdict
  >  ````python
  >  class Tree(dict):
  >     def __missing__(self, key):
  >         value = self[key] = self.__class__()
  >         return value
  >     __getattr__ = dict.__getitem__
  >     __setattr__ = dict.__setitem__
  >
  >  tree = Tree()
  >  tree.aaaaa.bbbbb.cccccc
  >  tree.aaaaa.b2222222.ccccw = 9
  >  print (tree)
  >  prttree(tree) # see more  
  >
  >  # {'aaaaa': {'b2222222': {'ccccw': 9}, 'bbbbb': {'cccccc': {}}}}
  >  #   0.> aaaaa
  >  #       1.> b2222222
  >  #           2.> ccccw
  >  #       1.> bbbbb
  >  #           2.> cccccc
  >  ````

  [prttree  see more](/dict(defaultdict_missing)_creat_Tree.py)                                        ref1: [wikipedia ](https://en.wikipedia.org/wiki/Autovivification#Python)   ref2 : [gist hrldcpr ](https://gist.github.com/hrldcpr/2012250)

  ​

  eg2 :  attr to url

  ~~~python
  class Url(str):
      __add__ = lambda self,name: Url(str.__add__(self, "/" + str(name)))
      __getattr__ = __add__

  url_path = Url('https://github.com').willowj.py_tricks.master + 5 + 8 + 9

  print(url_path)
  # https://github.com/willowj/py_tricks/master/5/8/9
  ~~~

  ​

### SUM with start param

- > ~~~python
  > lis =  [[1, 2, 3], [4, 5, 6], [7, 8, 9], [1, 5], [5, [9]]]
  >
  > reduce(lambda x,y:x+y,i)
  > sum(lis,[])  # little quicker than reduce and for loop
  >
  > #[1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 5, 5, [9]]
  > #[1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 5, 5, [9]]
  > ~~~

  sum(sequence[, start]) -> value

  Return the sum of a sequence of numbers (NOT strings) plus the value of parameter 'start' (which **defaults to 0**).  

  When the sequence is  empty,  return start.
  Type:      builtin_function_or_method

  [ref](https://www.zhihu.com/question/27376156/answer/220768257)



### `IF else`  <-> `and or`   一行条件判断

- > ~~~python
  > a = 0 
  > b = 7
  >
  > r1 = "a" if (a > b) else "b"	   # little slower in py3
  >
  > r2 = a > b and "a" or "b"          # little slower in py2, 
  > ~~~




###  Singleton 单例模式

​	 singleton decorator

- >~~~python
  >import threading
  >def singleton(cls):
  >    instances_dict = dict()
  >    _lock = threading.Lock()
  >    def wraper(*args, **kwargs):
  >        if cls not in instances_dict:
  >            with _lock :
  >                if cls not in instances_dict:
  >                    instances_dict[cls] = cls(*args, **kwargs)
  >                else:
  >                    instances_dict[cls].__init__(*args, **kwargs)
  >        return instances_dict[cls]
  >    return wraper
  >
  >@singleton
  >class Test(object):pass
  >
  >Test() is Test()
  >~~~

  ​


### collection

- > | [`namedtuple()`](https://docs.python.org/3.6/library/collections.html#collections.namedtuple) | factory function for creating tuple subclasses with named fields |
  > | ---------------------------------------- | ---------------------------------------- |
  > | [`deque`](https://docs.python.org/3.6/library/collections.html#collections.deque) | list-like container with fast appends and pops on either end |
  > | [`ChainMap`](https://docs.python.org/3.6/library/collections.html#collections.ChainMap) | dict-like class for creating a single view of multiple mappings |
  > | [`Counter`](https://docs.python.org/3.6/library/collections.html#collections.Counter) | dict subclass for counting hashable objects |
  > | [`OrderedDict`](https://docs.python.org/3.6/library/collections.html#collections.OrderedDict) | dict subclass that remembers the order entries were added |
  > | [`defaultdict`](https://docs.python.org/3.6/library/collections.html#collections.defaultdict) | dict subclass that calls a factory function to supply missing values |
  > | [`UserDict`](https://docs.python.org/3.6/library/collections.html#collections.UserDict) | wrapper around dictionary objects for easier dict subclassing |
  > | [`UserList`](https://docs.python.org/3.6/library/collections.html#collections.UserList) | wrapper around list objects for easier list subclassing |
  > | [`UserString`](https://docs.python.org/3.6/library/collections.html#collections.UserString) | wrapper around string objects for easier string subclassing |

### itertools 

​	


- > ~~~python
  > # Cartesian product
  > for p in itertools.product([1, 2, 3], [4, 5]):
  >     print(p)
  >     
  > (1, 4)
  > (1, 5)
  > (2, 4)
  > (2, 5)
  > (3, 4)
  > (3, 5)
  > ~~~




more :

​	[pythontips -intermediatePython ](http://book.pythontips.com/en/latest/index.html)  [中文版]( https://github.com/eastlakeside/interpy-zh/blob/master/SUMMARY.md)

​	[stackoverflow](https://stackoverflow.com/questions/101268/hidden-features-of-python)

​	[quora](https://www.quora.com/What-are-some-cool-Python-tricks)

​	[jobbole（zh）](http://blog.jobbole.com/63320/)

