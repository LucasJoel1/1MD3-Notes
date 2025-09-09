# Lecture 2 | Sept 9th 2025

## Booleans

### What is a boolean?

A boolean is a data type that only can hold 2 values, true and false and in python it is denoted with the syntax `True` and `False` (remember the capitalization).

### Boolean Expressions

A boolean is expression is an expression that will exvaluate to a boolean value, `True` or `False`.  There are a set of opperations available to use for us to evaluate these expressions.

|Symbol|Opperation|
|----|-----|
|`a == b`| Is `a` equal to `b`|
|`a != b`| Is `a` not equal to `b`|
|`a > b` | Is `a` greater than `b`|
|`a >= b`| Is `a` greater than or equal to `b`|
|`a < b` | Is `a` less than `b`|
|`a <= b` | Is `a` less than or equal to `b`|

```py
1 == 2
# false
2 == 2
# true

1 != 2
# true
2 != 1
#false

1 > 2
# false
2 > 1
# true
2 > 2
# false

1 >= 2
# false
2 >= 1
# true
2 >= 2
# true

# greater than and greater than and equal to work the same way for less than and less than or equal to just reversed

i.e.

2 > 1
# true
2 < 1
# false

# these opperations can also be chained together in python

2 > 1 > 0
# true

2 < 1 < 2
# false
```

We also have other opperations that instead of taking in something like an integer and comparing the equality, it takes in a boolean expression or a boolean itself and uses that.  These are `and`, `or`, and `not`.

|Symbol|Opperation|
|------|----------|
|`a and b`| Checks if `a` **and** `b` are both `True`|
|`a or b` | Checks if `a` **or** `b` are both `True` |
| `not a` | Inverts the value of `a`|

```py
True and True
# True
True and False
# False
False and False
# False

True or True
# True
True or False
# True
False or True
# True
False or False
# False

not True
# False
not False
# True
not not True
# True

# We can use the earlier opperators like equal to and such with and, or and not
```

You can use these expressions on variable assignment

```py
x = True
y = False

a = x or y
# True
b = not x
# False
c = x and y
# False
```

You can also use boolean expressions with arithmatic

```py
2 + 4 > 3 - 2 and 2 + 2 <= 2 * 2
# let's go step by step on how the interpreter would look at this

# first we go through all our aritmatic following BEDMAS

6 > 1 and 4 <= 4

# Next we do our relational opperators

True and True

# Finally we do our logical opperators

True
```

### XOR vs OR

`xor` and `or` are very similar and share or's key property of if 1 of the values is `True`, the output will be `True` and if both are `False` the output will be false.  The key difference between the 2 is in one case where in if both values are `True` the output will be `True` while with `xor` if both values are `True` the output will be `False` which is why it is called exclusive.  Below are the truth tables for both `or` and `xor` so see the difference

**OR**

|Expression|Value|
|----------|-----|
|`False` or `False` | `False` |
|`True` or `False` | `True` |
|`False` or `True` | `True` |
|`True` or `True` | **`True`** |

**XOR**

|Expression|Value|
|----------|-----|
|`False` or `False` | `False` |
|`True` or `False` | `True` |
|`False` or `True` | `True` |
|`True` or `True` | **`False`** |

Note that `xor` does not exist in python in relation to `or`, `and` and `not` however the exact same truth table is created with `a != b`.

**IMPORTANT: YOU WILL NOT BE TESTED ON XOR BUT IT IS GOOD TO KNOW**

### Simplified Boolean Expressions

```py
a or True
= True

a or False
= a

a and True
= a

a and False
= False

a or (not a)
= True

a and (not a)
= False
```