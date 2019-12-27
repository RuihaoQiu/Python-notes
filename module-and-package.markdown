# Python module and package

### Python module

example.py

```
s = "If Comrade Napoleon says it, it must be right."
a = [100, 200, 300]

def foo(arg):
    print(f'arg = {arg}')

class Foo:
    pass
    
if (__name__ == '__main__'):
	"""execute as standalone script"""
    print('Executing as standalone script')
    print(s)
    print(a)
    foo('quux')
    x = Foo()
    print(x)
```



execute example

```
>>> import example
>>> print(mod.s)
If Comrade Napoleon says it, it must be right.
>>> example.a
[100, 200, 300]
>>> example.foo(['quux', 'corge', 'grault'])
arg = ['quux', 'corge', 'grault']
>>> x = example.Foo()
>>> x
<example.Foo object at 0x03C181F0>

>>> from example import s, foo
>>> s
'If Comrade Napoleon says it, it must be right.'
>>> foo('quux')
arg = quux

>>> from example import Foo
>>> x = Foo()
>>> x
<example.Foo object at 0x02E3AD50>

>>> import mod as my_module
>>> my_module.a
[100, 200, 300]
>>> my_module.foo('qux')
arg = qux
```

run as standalone script

```
C:\Users\john\Documents>python fact.py 6
720
```



#### The Module Search Path

```
import example
```

```
>>> import sys
>>> sys.path
['', 'C:\\Users\\john\\Documents\\Python\\doc', 'C:\\Python36\\Lib\\idlelib',
'C:\\Python36\\python36.zip', 'C:\\Python36\\DLLs', 'C:\\Python36\\lib',
'C:\\Python36', 'C:\\Python36\\lib\\site-packages']

>>> sys.path.append(r'C:\Users\john')
>>> sys.path
['', 'C:\\Users\\john\\Documents\\Python\\doc', 'C:\\Python36\\Lib\\idlelib',
'C:\\Python36\\python36.zip', 'C:\\Python36\\DLLs', 'C:\\Python36\\lib',
'C:\\Python36', 'C:\\Python36\\lib\\site-packages', 'C:\\Users\\john']
>>> import example

>>> import example
>>> mod.__file__
'C:\\Users\\john\\mod.py'

>>> import re
>>> re.__file__
'C:\\Python36\\lib\\re.py'

```

add path permanently, in .profile add

``` 
export PYTHONPATH = "path"
```



reload module

```
>>> import example
>>> import importlib
>>> importlib.reload(example)
```



### Python Package

mod1.py

```
def foo():
    print('[mod1] foo()')

class Foo:
    pass
```

mod2.py

```
def bar():
    print('[mod2] bar()')

class Bar:
    pass
```

execute

```
>>> import pkg.mod1, pkg.mod2
>>> pkg.mod1.foo()
[mod1] foo()
>>> x = pkg.mod2.Bar()
>>> x
<pkg.mod2.Bar object at 0x033F7290>

>>> from pkg.mod1 import foo
>>> foo()
[mod1] foo()

>>> from pkg.mod2 import Bar as Qux
>>> x = Qux()
>>> x
<pkg.mod2.Bar object at 0x036DFFD0>
```



#### Package Initialization

If a file named `__init__.py` is present in a package directory, it is invoked when the package or a module in the package is imported. This can be used for execution of package initialization code, such as initialization of package-level data.

\__init.py__

```
print(f'Invoking __init__.py for {__name__}')
A = ['quux', 'corge', 'grault']

print(f'Invoking __init__.py for {__name__}')
import pkg.mod1, pkg.mod2
```

```
>>> import pkg
Invoking __init__.py for pkg
>>> pkg.A
['quux', 'corge', 'grault']

>>> pkg.mod1.foo()
[mod1] foo()
>>> pkg.mod2.bar()
[mod2] bar()
```

if \__init__ contains:

```
__all__ = [
        'mod1',
        'mod2',
        'mod3',
        'mod4'
        ]
```

```
>>> dir()
['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__',
'__package__', '__spec__']

>>> from pkg import *
>>> dir()
['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__',
'__package__', '__spec__', 'mod1', 'mod2', 'mod3', 'mod4']
>>> mod2.bar()
[mod2] bar()
>>> mod4.Qux
<class 'pkg.mod4.Qux'>
```



REF

https://realpython.com/python-modules-packages/