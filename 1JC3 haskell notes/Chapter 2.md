# Chapter 2 - Functions

## Calling Functions

In the previous chapter we have already been calling functions.  The `*` is a function that takes 2 numbers and multiplies them.  This is called an infix function where we put the symbol between the 2 values we want to multiply.  Most functions are called prefix functions where you put the function name then values you want to pass in. Examples of prefix functions are the min and max functions which each take in 2 numbers and returns the lowest or highest of the two respectively.

```haskell
min 9 10
-- 9

max 9 10
-- 10
```

Functions can be passed into each other, and the result of one function can be used as the argument of another. Function application has the highest precedence in Haskell, so `f x + y` is read as `(f x) + y`, not `f (x + y)`.

```haskell

max (min 5 4) 3
-- 4

max 5 4 + min 4 5 + 1
-- 10
-- is the same as
(max 5 4) + (min 4 5) + 1

-- this also means that if we want to pass in arithmetic into a function it has to be wrapped in brackets

succ 9 * 10 -- succ gets the value following the input or "successor"
-- 100 ((9 + 1 = 10) * 10 = 100)

succ (9 * 10)
-- 91 ((9 * 10) + 1) = 91
```

a prefix function can also be called as an infix function if the name is surrounded by backticks (\`) here is an example using the div function

```haskell
div 25 5
-- 5

25 `div` 5
-- 5
```

an infix function can also be a prefix function with brackets

```haskell
(+) 1 2
-- 3
```

in cases like this it can make it more clear which number is divided by which

## Creating Functions

Creating a function is similar to calling a function.  Let's create a function that takes a number and doubles it

```haskell
doubleNumber x = x + x
```

let's go over this syntax

`doubleNumber` is the name of the function

`x` is the name of the parameter we are passing in, since there is only one parameter here our function only takes in one parameter

`=` sets the function equal to the following expression

`x+x` adds the two values and outputs the result

for a multi line function haskell uses indentation like python

```haskell
newMax x y =
    if x > y then x
    else y

newMax 1 2
-- 2
```

this function takes in 2 values `x, y` and then using if statements (which we will go over in the next chapter) will return the higher of the two values

Functions also can have defined parameter and resulting types.  The following is the syntax for defining a function that takes in an Int with a resulting value of an Int

```haskell
myFunc :: Int -> Int -- first int is for the param, second for the resulting value type
myFunc x = x + 1

-- subsequent param types can be formatted as the following
myFunc2 :: Int -> Int -> Int
myFunc2 x y = x + y

-- takes in Int x
-- takes in Int y
-- outputs x + y as an Int
```
    