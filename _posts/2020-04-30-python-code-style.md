---
layout: post
title: "Python Coding Style"
# subtitle: 
# image: /img/avatar-icon.jpg
tag: [coding, coding_skill]
# bigimg:
---

# 1. Introduction
I started coding 15 years ago. During this 15 years, I spent most of the time in the academic domain. No one forces me to follow the coding style. Although I learned some small skills fo coding sometimes, it's not systematical. Now I would like to study the coding style of Python and note the points  in the post. The main references are Pep 8 Python Style[[1]](#1) and Google Python Style[[2]](#2).

# 2. Consistency
**One of Guido's key insights is that code is read much more often than it is written. **

# 3. Code-layout
## 3-1. Indentation
4 spaces
## 3-2. Maximum Line Length
Limit all lines to a maximum of 79 (80) characters.


Break the line before the binary operator
```python
# Correct:
# easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```
## 3-3. Blank Lines
Surround top-level function and class definitions with two blank lines.

Method definitions inside a class are surrounded by a single blank line.

Use blank lines in functions, sparingly, to indicate logical sections.

## 3-4. Imports
Imports should usually be on separate lines

```python
# Correct:
import os
import sys

# Wrong:
import sys, os

# Correct:
from subprocess import Popen, PIPE
```

Imports should be grouped in the following order:

Standard library imports.
Related third party imports.
Local application/library specific imports.
You should put a **blank line** between each group of imports.

Absolute imports are recommended.

## 3-5. Module Level Dunder Names
Module level "dunders" (i.e. names with two leading and two trailing underscores) such as __all__, __author__, __version__, etc. should be placed after the module docstring but before any import statements except from __future__ imports. Python mandates that future-imports must appear in the module before any other code except docstrings:

```python
"""This is the example module.

This module does stuff.
"""

from __future__ import barry_as_FLUFL

__all__ = ['a', 'b', 'c']
__version__ = '0.1'
__author__ = 'Cardinal Biggles'

import os
import sys

```

# 4. Whitespace in Expressions and Statements
**Avoid** extraneous whitespace in the following situations:
**Immediately inside parentheses, brackets or braces**
```python
# Correct:
spam(ham[1], {eggs: 2})

# Wrong:
spam( ham[ 1 ], { eggs: 2 } )
```

**Between a trailing comma and a following close parenthesis**
```python
# Correct:
foo = (0,)

# Wrong:
bar = (0, )
```

**Immediately before a comma, semicolon, or colon**
```python
# Correct:
if x == 4: print x, y; x, y = y, x  

# Wrong:
if x == 4 : print x , y ; x , y = y , x
```

**However, in a slice the colon acts like a binary operator, and should have equal amounts on either side (treating it as the operator with the lowest priority). In an extended slice, both colons must have the same amount of spacing applied. Exception: when a slice parameter is omitted, the space is omitted**

```python
# Correct:
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
ham[lower:upper], ham[lower:upper:], ham[lower::step]
ham[lower+offset : upper+offset]
ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
ham[lower + offset : upper + offset]

# Wrong:
ham[lower + offset:upper + offset]
ham[1: 9], ham[1 :9], ham[1:9 :3]
ham[lower : : upper]
ham[ : upper]
```

**If operators with different priorities are used, consider adding whitespace around the operators with the lowest priority(ies). Use your own judgment; however, never use more than one space, and always have the same amount of whitespace on both sides of a binary operator**
```python
# Correct:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

# Wrong:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

**When combining an argument annotation with a default value, however, do use spaces around the = sign:**
```python
# Correct:
def munge(sep: AnyStr = None): ...
def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...

# Wrong:
def munge(input: AnyStr=None): ...
def munge(input: AnyStr, limit = 1000): ...

```
**When trailing commas are redundant, they are often helpful when a version control system is used, when a list of values, arguments or imported items is expected to be extended over time. The pattern is to put each value (etc.) on a line by itself, always adding a trailing comma, and add the close parenthesis/bracket/brace on the next line. However it does not make sense to have a trailing comma on the same line as the closing delimiter (except in the above case of singleton tuples):**

```python
# Correct:
FILES = [
    'setup.cfg',
    'tox.ini',
    ]
initialize(FILES,
           error=True,
           )

# Wrong:
FILES = ['setup.cfg', 'tox.ini',]
initialize(FILES, error=True,)
```

# 5. Comments
Comments should be complete sentences. The first word should be capitalized, unless it is an identifier that begins with a lower case letter (never alter the case of identifiers!).


## 5-1. Documentation Strings

```python
"""Return a foobang

Optional plotz says to frobnicate the bizbaz first.
"""
```

# 6. Naming Conventions

## 6-1. Descriptive: Naming Styles
The following naming styles are commonly distinguished:

b (single lowercase letter)

B (single uppercase letter)

lowercase

lower_case_with_underscores

UPPERCASE

UPPER_CASE_WITH_UNDERSCORES

CapitalizedWords (or CapWords, or CamelCase -- so named because of the bumpy look of its letters [4]). This is also sometimes known as StudlyCaps.

Note: When using acronyms in CapWords, capitalize all the letters of the acronym. Thus HTTPServerError is better than HttpServerError.

mixedCase (differs from CapitalizedWords by initial lowercase character!)

Capitalized_Words_With_Underscores (ugly!)

## 6-2. Class Names
Class names should normally use the CapWords convention.

## 6-3. Type Variable Names
Names of type variables introduced in PEP 484 should normally use CapWords preferring short names: T, AnyStr, Num.

```python
from typing import TypeVar

VT_co = TypeVar('VT_co', covariant=True)
KT_contra = TypeVar('KT_contra', contravariant=True)
```

## 6-4. Function and Variable Names
Function names should be lowercase, with words separated by underscores as necessary to improve readability.

Variable names follow the same convention as function names.

## 6-5. Method Names and Instance Variables
Use the function naming rules: lowercase with words separated by underscores as necessary to improve readability.

Use one leading underscore only for non-public methods and instance variables.

To avoid name clashes with subclasses, use two leading underscores to invoke Python's name mangling rules.


## 6-6. Constants
Constants are usually defined on a module level and written in all capital letters with underscores separating words. Examples include MAX_OVERFLOW and TOTAL.


# 7. Practice
## 7-1. Lambda Functions
Okay for one-liners.

## 7-2. Conditional Expressions
Okay for simple cases.

## 7-3. Properties
Use properties for accessing or setting data where you would normally have used simple, lightweight accessor or setter methods.

## 7-4. Function and Method Decorators
Use decorators judiciously when there is a clear advantage. Avoid @staticmethod and limit use of @classmethod.

Never use @staticmethod unless forced to in order to integrate with an API defined in an existing library. Write a module level function instead.

Use @classmethod only when writing a named constructor or a class-specific routine that modifies necessary global state such as a process-wide cache.

## 7-5. from __future__ imports
Use of from __future__ import statements is encouraged. All new code should contain the following and existing code should be updated to be compatible when possible:
```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function
```

## 7-6. Type Annotated Code
```python
def func(a: int) -> List[int]:
```

## 7-7. Explicit exceptions to the 80 character limit:

1. Long import statements.
2. URLs, pathnames, or long flags in comments.
3. Long string module level constants not containing whitespace that would be inconvenient to split across lines such as URLs or pathnames.
4. Pylint disable comments. (e.g.: # pylint: disable=invalid-name)

Do not use backslash line continuation except for with statements requiring three or more context managers
```python
Yes:  with very_long_first_expression_function() as spam, \
           very_long_second_expression_function() as beans, \
           third_thing() as eggs:
          place_order(eggs, beans, spam, beans)

No:  with VeryLongFirstExpressionFunction() as spam, \
          VeryLongSecondExpressionFunction() as beans:
       PlaceOrder(eggs, beans, spam, beans)

Yes:  with very_long_first_expression_function() as spam:
          with very_long_second_expression_function() as beans:
              place_order(beans, spam)

```

When a literal string won’t fit on a single line, use parentheses for implicit line joining.
```python
x = ('This will build a very long long '
     'long long long long long long string')
```

## 7-8. Parentheses
Use parentheses sparingly.

It is fine, though not required, to use parentheses around tuples. Do not use them in return statements or conditional statements unless using parentheses for implied line continuation or to indicate a tuple.
```python
Yes: if foo:
         bar()
     while x:
         x = bar()
     if x and y:
         bar()
     if not x:
         bar()
     # For a 1 item tuple the ()s are more visually obvious than the comma.
     onesie = (foo,)
     return foo
     return spam, beans
     return (spam, beans)
     for (x, y) in dict.items(): ...

No:  if (x):
         bar()
     if not(x):
         bar()
     return (foo)

```

## 7-9. Indentation
```python
Yes:   # Aligned with opening delimiter
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)
       meal = (spam,
               beans)

       # Aligned with opening delimiter in a dictionary
       foo = {
           long_dictionary_key: value1 +
                                value2,
           ...
       }

       # 4-space hanging indent; nothing on first line
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)
       meal = (
           spam,
           beans)

       # 4-space hanging indent in a dictionary
       foo = {
           long_dictionary_key:
               long_dictionary_value,
           ...
       }
```

## 7-10. Shebang Line
Most .py files do not need to start with a #! line. Start the main file of a program with #!/usr/bin/python with an optional single digit 2 or 3 suffix per PEP-394.



## Reference
<a id="1">[1]</a> 
<a href="https://www.python.org/dev/peps/pep-0008/">PEP 8 -- Style Guide for Python Code </a>

<a id="2">[2]</a> 
<a href="http://google.github.io/styleguide/pyguide.html">Google Python Style Guide</a>

