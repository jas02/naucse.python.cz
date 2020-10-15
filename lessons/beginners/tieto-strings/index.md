## Strings

All standard sequential operations (indexing, slicing, multiplication, membership, length, minimum, maximum) are also applicable to strings.

Keep in mind, however, that strings are immutable, so the following code will not work.

```
>>> website = 'http://www.python.org'
>>> website[-3:] = 'com'
Traceback (most recent call last):
  File "<pyshell#19>", line 1, in ?
  website[-3:] = 'com'
TypeError: object doesn't support slice assignment
```

## Formatting strings

One of the methods is to print and format strings with the% operator, just like in C.

We can use string, integer, tuple or dictionary as the values we want to print.

```
>>> format = "Hello, %s. %s are you?"
>>> values = ('world', 'How')
>>> format % values
'Hello, world. How are you?'
```

%s is so called *conversion specifiers*. Indicates where to insert values from the right side of the assignment.

Other possible uscase:


```
%s - string
%i - integer
%f - floating point
```

The latest and recommended way to format strings is to use the *format()* method. Each string entry we want to format is represented by braces *{}* and can contain a name as well as information on how to format the string correctly.

```
>>> "{}, {} and {}".format("first", "second", "third")
'first, second and third'
>>> "{0}, {1} and {2}".format("first", "second", "third")
'first, second and third'
```

We can also format as follows:

```
>>> "{3} {0} {2} {1} {3} {0}".format("be", "not", "or", "to")
'to be or not to be'
```
We can also name the values:


```
>>> from math import pi
>>> "{name} is approximately {value:.2f}.".format(value=pi, name="π")
'π is approximately 3.14.'
```

*.2f* means that the number will be printed to two decimal places.

As of Python 3.6, we can also format a string as follows:

```
>>> from math import e
>>> f"Euler's constant is roughly {e}."
"Euler's constant is roughly 2.718281828459045."
```

For example, another option is:

```
>>> name = 'Fred'
>>> age = 42
>>> f'He said his name is {name} and he is {age} years old.'
He said his name is Fred and he is 42 years old.
```

We can even use Python expressions and methods in braces:

```
>>> name = 'Fred'
>>> seven = 7
>>> f'''He said his name is {name.upper()}
...    and he is {6 * seven} years old.'''
'He said his name is FRED\n    and he is 42 years old.'
```

The older equivalent of the same code is:

```
>>> "Euler's constant is roughly {e}.".format(e=e)
"Euler's constant is roughly 2.718281828459045."
```

String formatting (format function) uses a template language. Each value to be replaced is stored in compound quotation marks *{}*, called *replacement fields*. If we want to list the compound quotes in the list, we have to do it like this:

{% raw %}
```
>>> "{{ double braces }}".format()
'{ double braces }'
```
{% endraw %}

###  Replacement Fields

They consist of:

**Field name** - index or identifier

**Conversion flag** - Exclamation mark followed by one character

* r - repr
* s - string
* a - ascii

**Format specifier** - a colon followed by an expression of the templating language

Examples:

```
>>> "{foo} {} {bar} {}".format(1, 2, bar=4, foo=3)
'3 1 4 2'
```

We can also access only the part of the value (field) that we want to print:

```
>>> fullname = ["Alfred", "Hitchcock"]
>>> "Mr {name[1]}".format(name=fullname)
'Mr Hitchcock'
```

### Basic conversion

```
>>> print("{pi!s} {pi!r} {pi!a}".format(pi="π"))
π 'π' '\u03c0'
```

Floating point *format specifier*

```
>>> "The number is {num}".format(num=42)
'The number is 42'
>>> "The number is {num:f}".format(num=42)
'The number is 42.000000'
```

Binary *format specifier*

```
>>> "The number is {num:b}".format(num=42)
'The number is 101010'
```

**Format specifier**

* b - binary
* c - integer
* d - integer print as decimal
* f - decimal with a fixed number of decimal places
* o - integer as an octal number


### Alignment width

```
>>> "{num:10}".format(num=3)
'         3'
>>> "{name:10}".format(name="Bob")
'Bob       '
```

### Precison

```
>>> "Pi is {pi:.2f}".format(pi=pi)
'Pi is 3.14'
```

Aligned formatting:

```
>>> "{pi:10.2f}".format(pi=pi)
'      3.14'
```

Alignment accuracy can also be used as follows:

```
>>> "{:.5}".format("Guido van Rossum")
'Guido'
```

We can specify several types of alignment.

Zero-padded:

```
>>> '{:010.2f}'.format(pi)
'0000003.14'
```

Left, right, centered:

```
>>> print('{0:<10.2f}\n{0:^10.2f}\n{0:>10.2f}'.format(pi))
3.14
   3.14
      3.14
```

We can specify with which character we fill in the blanks, as a replacement for the space:

```
>>> "{:$^15}".format(" I WON ")
'$$$$ I WON $$$$'
```

How to format signed numbers?

```
>>> print('{0:-.2}\n{1:-.2}'.format(pi, -pi)) # Default
3.1
-3.1
>>> print('{0:+.2}\n{1:+.2}'.format(pi, -pi))
+3.1
-3.1
>>> print('{0: .2}\n{1: .2}'.format(pi, -pi))
 3.1
-3.1
```

Practical example:

{% raw %}

```
# Print a formatted price list with a given width

width = int(input('Please enter width: '))

price_width = 10
item_width  = width - price_width

header_fmt = '{{:{}}}{{:>{}}}'.format(item_width, price_width)
fmt        = '{{:{}}}{{:>{}.2f}}'.format(item_width, price_width)

print('=' * width)

print(header_fmt.format('Item', 'Price'))

print('-' * width)

print(fmt.format('Apples', 0.4))
print(fmt.format('Pears', 0.5))
print(fmt.format('Cantaloupes', 1.92))
print(fmt.format('Dried Apricots (16 oz.)', 8))
print(fmt.format('Prunes (4 lbs.)', 12))                                                                              

print('=' * width)
```

{% endraw %}


Output:

```
Please enter  width: 35
===================================
Item                          Price
-----------------------------------
Apples                         0.40
Pears                          0.50
Cantaloupes                    1.92
Dried  Apricots (16 oz.)       8.00
Prunes (4 lbs.)               12.00
===================================
```

## String methods

### center()

```
>>> "The Middle by Jimmy Eat World".center(39)
'     The Middle by Jimmy Eat World     '
>>> "The Middle by Jimmy Eat World".center(39, "*")
'*****The Middle by Jimmy Eat World*****'
```

### find()

Returns the left index on which the string was found.

```
>>> 'With a moo-moo here, and a moo-moo there'.find('moo')
7
>>> title = "Monty Python's Flying Circus"
>>> title.find('Monty')
0
>>> title.find('Python')
6
>>> title.find('Flying')
15
>>> title.find('Zirquss')
-1
```

### join()

```
>>> seq = [1, 2, 3, 4, 5]
>>> sep = '+'
>>> sep.join(seq) # Trying to join a list of numbers
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: sequence item 0: expected string, int found
>>> seq = ['1', '2', '3', '4', '5']
>>> sep.join(seq) # Joining a list of strings
'1+2+3+4+5'
>>> dirs = '', 'usr', 'bin', 'env'
>>> '/'.join(dirs)
'/usr/bin/env'
>>> print('C:' + '\\'.join(dirs))
C:\usr\bin\env
```
Inverse function is *split()*.

### lower()

Returns the lowercase version of the string:

```
>>> 'Dance Floor'.lower()
'dance floor'
```

Reverse function is *upper()*.

### replace()

All occurrences of the search string are replaced.

```
>>> 'This is a test'.replace('is', 'eez')
'Theez eez a test'
```

### split()

```
>>> '1+2+3+4+5'.split('+')
['1', '2', '3', '4', '5']
>>> '/usr/bin/env'.split('/')
['', 'usr', 'bin', 'env']
>>> 'Using   the   default'.split()
['Using', 'the', 'default']
```

### strip()

Returns a string without spaces at the beginning and end.

```
>>> '    internal whitespace is kept    '.strip()
'internal whitespace is kept'
```

