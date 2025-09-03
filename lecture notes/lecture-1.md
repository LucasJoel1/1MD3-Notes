# Lecture 1 | Sept 3rd 2025

## Python Math

Math in python is done in the following syntax

```py
# Addition
2 + 3
# 5

# Subtraction
3 - 2
# 1

# Multiplication
3 * 2
# 6

# Division (floating point)
4 / 2
# 2.0

# Integer division
3 // 2
# 1 (always rounds down)

# Floor division (finds remainder)
3 % 2
# 1

# Exponentation
3 ** 2
# OR
pow(3, 2)
# 9

# BEDMAS
2 + 2 * 2
# 6

(2 + 2) * 2
# 8
```

### Notes on python math
- regular division will output as a float always, even with whole nunmbers, for integer division use `//`
- python follows bedmas, you can use brackets to change the order of opperations like in regular math
- when doing exponents python will go right to left  so for `3**2**4` python will first evaluate `4**5` which is 16, then do `3**16` which is `43046721`

## Python Variables

### Creating and Assigning Variables

To assign a variable in python the syntax is the following
```python
x = 5
```

This will create a new variable called x and assign it the value of 5 (note that if a variable called x already exists, it will reassign x to the new value you set)

You can do arrithmatic on and with variables using the syntax in the [Python Math](#python-math) section.

```python
x = 3
y = x + 1 # 4
x = 5 # y is still 4
```

Even if you reassign the variable x when using it with variable y, it will use the previous value of x as python is a language that runs code top down and (in our case) will only access the value of x.  If the reassignment of x is before assigning y however, it will use the new value of x.

```python
x = 3
x = 5
y = x + 1 # value is 6 because reassignment happended before assigning value of y
```

### Swapping values of 2 variables

**Way 1**

The first way you can reassign a variable in python is by using a temperary variable

```py
x = 5 
y = 2
temp = x # setting to x temperarely
x = y # x loses old value and is now 2
y = temp # y is assigned to the temp value since x is currently set to the value of y
```

**Way 2**

Python has some special syntax that allows us to sway variables in one line

```py
x = 5
y = 2

x, y = y, x # note the order that the variables are listed are opposite between left and right side
```

**Way 3(advanced not reccomended for beginners)**

You can also use something known as a bitwise opperaiton to swap values.  This way uses a method that a computer is very fast at opperating however is advanced and beyond the scope of this course (written here for fun)

```py
x = 2
y = 3

x = x ^ y
y = x ^ y
x = x ^ y
```