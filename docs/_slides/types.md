---
---

## Data types

The immutable data types are

| `'int'`   | Integer            |
| `'float'` | Real number        |
| `'str'`   | Character string   |
| `'bool'`  | `True`/`False`     |
| `'tuple'` | Immutable sequence |

Any object can be queried with `type()` 


~~~python
>>> t = ('x', 3, True)

~~~
{:.output}



~~~python
>>> type(t)
<class 'tuple'>

~~~
{:.output}



===

Python supports the usual arithmetic operators for numeric types:

| `+`  | addition                |
| `-`  | subtraction             |
| `*`  | multiplication          |
| `/`  | floating-point division |
| `**` | exponent                |
| `%`  | modulus                 |
| `//` | floor division          |

===

Some operators have natural extensions to non-numeric types:


~~~python
>>> a * 2
'xyzxyz'

~~~
{:.output}




~~~python
>>> t + (3.14, 'y')
('x', 3, True, 3.14, 'y')

~~~
{:.output}



===

Comparison operators are symbols or plain english:

| `==`       | equal                             |
| `!=`       | non-equal                         |
| `>`, `<`   | greater, lesser                   |
| `>=`, `<=` | greater or equal, lesser or equal |
| `and`      | logical and                       |
| `or`       | logical or                        |
| `not`      | logical negation                  |
| `in`       | logical membership                |

===

## Exercise 1

Explore the use of `in` to test membership. What can an object of type `'int'` be a member of? Is it the same for an object of type `'str'`?