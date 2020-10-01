## Differences betweenPython 2 and Python 3

### print() is a function
Probably most visible diffenrence between Python 2 and Python 3. Command *print* has been replaced by *function* print()


**Python 2**


```
print 'Hello, World!'
print('Hello, World!')
print "text", ; print 'print more text on the same line'
```

```
Hello, World!
Hello, World!
text print more text on the same line
```

**Python 3**

```
print('Hello, World!')

print("some text,", end="")
print(' print more text on the same line')
```

```
Hello, World!
some text, print more text on the same line
```

```
print 'Hello, World!'
```

```
File "<ipython-input-3-139a7c5835bd>", line 1
    print 'Hello, World!'
                        ^
SyntaxError: invalid syntax
```

### Division by integers

Integer division behaves differently in Python 2 and Python 3.

**Python 2**

```
print '3 / 2 =', 3 / 2
print '3 // 2 =', 3 // 2
print '3 / 2.0 =', 3 / 2.0
print '3 // 2.0 =', 3 // 2.0
```

```
3 / 2 = 1
3 // 2 = 1
3 / 2.0 = 1.5
3 // 2.0 = 1.0
```

**Python 3**

```
print('3 / 2 =', 3 / 2)
print('3 // 2 =', 3 // 2)
print('3 / 2.0 =', 3 / 2.0)
print('3 // 2.0 =', 3 // 2.0)
```

```
3 / 2 = 1.5
3 // 2 = 1
3 / 2.0 = 1.5
3 // 2.0 = 1.0
```

### Unicode Support

Python 2 has separate types for str (), these are ASCII characters and then unicode (). In Python 3, all str () strings are Unicode characters by default. Next, Python 3 introduces byte support.

### Raise an exception

In Python 2, there are two ways to raise an exception. Python 3 allows only one.

**Python 2**

```
raise IOError, "file error"
```

```
raise IOError, "file error"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: file error
```

```
raise IOError("file error")
```

```
raise IOError("file error")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: file error
```

**Python 3**

The following notation in Python 3 does not work:

```
raise IOError, "file error"
```

```
raise IOError, "file error"
  File "<stdin>", line 1
    raise IOError, "file error"
                 ^
SyntaxError: invalid syntax
```
The only correct entry is this:

```
raise IOError("file error")
```

```
raise IOError("file error")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OSError: file error
```

### Exception handling

The treatment of exceptions has also changed. See how exceptions are handled in Python 2 and Python 3.

**Python 2**

```
try:
    let_us_cause_a_NameError
except NameError, err:
    print err, '--> our error message'
```

```
name 'let_us_cause_a_NameError' is not defined --> our error message
```

**Python 3**

```
try:
    let_us_cause_a_NameError
except NameError as err:
    print(err, '--> our error message')
```

```
name 'let_us_cause_a_NameError' is not defined --> our error message
```

### User inputs

In Python 2, there are two ways to get user input. input() function and raw_input() function. The problem with the input() function is that it can be potentially dangerous because it does not always return a string.

**Python 2**

```
Python 2.7.6
[GCC 4.0.1 (Apple Inc. build 5493)] on darwin
Type "help", "copyright", "credits" or "license" for more information.

>>> my_input = input('enter a number: ')

enter a number: 123

>>> type(my_input)
<type 'int'>

>>> my_input = raw_input('enter a number: ')

enter a number: 123

>>> type(my_input)
<type 'str'>
```

**Python 3**

```
Python 3.7.0 (default, Aug 24 2018, 20:34:01)
[Clang 9.0.0 (clang-900.0.39.2)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> my_input = input('enter a number: ')
enter a number: 123
>>> type(my_input)
<class 'str'>
```
