# Lecture 1 | Sept 5th 2025

## Python Math Continued

### Example 1

```python
x = 1 + 4
# x = 5 (adding 1 + 4)
y = x - 1
# y = 4 (subtracting 1 from x which is 5)
y = y + 1 * x
# y = 9 (using bedmas 1 * x is 5 then adding y which is currently 4)
x = y // x
# x = 1 (integer division always rounding down (1.8) => 1)

# x: 1
# y: 9
```

### Example 2

```python
x = 1
# x = 1 (set x to 1)
y = x + x
# y = 2 (y is x + x where x is 1)
z = y + y + 1.0
# z = 5.0 (y + y where y is 2 + 1.0 casted to float because of + 1.0)
y = y // x
# y = 2 (integer division of y / x where y is 2 and x is 1)
x = z // x
# x = 5.0 (z integer divided by x where z is 5.0 and x is 1, casted to float due to 5.0.  integer division keeps the type rule of casting to float if there is a float)
z = x + x/4
# z = 6.25 (divide x which is 5.0 by 4 first because of bedmas then add x)
y = y**((y*y) % 3)
y = y**((4) % 3) # first multiply y which is 2 by itself
y = y**(1) # then take the modulo of 4 and 3
# y = 2 (y which is 2 to the power of 1 is 2)

# x: 5.0
# y: 2
# z: 6.25
```

## Creating a Program (Hello World)

```py
print("Hello World")
```

Running this by double clicking on the desktop will cause a terminal window to flash witht the text hello world then close.  This is not the intended us of this program.  We can fix this by adding one line.

```py
print("Hello World")
input("Press enter to quit...")
```

Now if we run this the terminal window will wait for a key from the keyboard to be pressed (any key works, not just enter) and once a key has been pressed the window will close

```py
print("************ Adder Program 24.11.3 ************")
num1 = input("Please enter the first number: ") # take in the first number
num2 = input("Please enter the second number: ") # take in the second number
print("Your number is: " + (num1 + num2)) # output num1 + num2
input("Please press enter to terminate") # wait for termination
```

While this program won't crash it does have a logic error.  When you take in an input it will automatically take it in as a string which is just a bunch of characters so by using the plus symbol we are taking the first string and putting the second one after (string concatination) it so if we have an input of the numbers 6 and 7 while we want 13 it will instead print 67

```py
print("************ Adder Program 24.11.3 ************")
num1 = input("Please enter the first number: ") # take in the first number
num2 = input("Please enter the second number: ") # take in the second number
print("Your number is: " + (int(num1) + int(num2))) # output num1 + num2
input("Please press enter to terminate") # wait for termination
```

In this next version while we fixed our logic error we introduced a new syntax error which will cause the program to throw us an error.  on the 4th line we are trying to perform string concatination with the wrong datatype (error found below).

```py
************ Adder Program 24.11.3 ************
Please enter the first number: 6
Please enter the second number: 7
Traceback (most recent call last):
  File "<python-input-2>", line 4, in <module>
    print("Your number is: " + (int(num1) + int(num2))) # output num1 + num2
          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~
TypeError: can only concatenate str (not "int") to str
```

To fix this we can wrap the 2 ints in the print statements in a str keyword to convert it which will make us first add the numbers, convert it to a string then concatinate the 2 string

```py
print("************ Adder Program 24.11.3 ************")
num1 = input("Please enter the first number: ") # take in the first number
num2 = input("Please enter the second number: ") # take in the second number
print("Your number is: " + str(int(num1) + int(num2))) # output num1 + num2 now wrapped in str to fix error
input("Please press enter to terminate") # wait for termination
```

```bash
************ Adder Program 24.11.3 ************
Please enter the first number: 6
Please enter the second number: 7
Your number is: 13
Please press enter to terminate

```

And we can now see that our program works