# Chapter 1 - Arithmatic

## Simple Arithmetic

```haskell

-- Addition
2 + 15
-- 17

-- Subtraction
15 - 2
-- 13

-- Multiplication
15 * 2
-- 30

-- Division
15 / 2
-- 7.5
```

If you have multiple opperators in an expression Haskell will use BEDMAS

```haskell
2 + 2 * 2
-- 6

(2 + 2) * 2
-- 8 (note the brackets)
```

If you are using negative numbers in an expression wrap the number and sign in brackets to prevent error

```haskell
2 + -2
-- will throw error
Precedence parsing error
    cannot mix ‘+’ [infixl 6] and prefix `-' [infixl 6] in the same infix expression

2 + (-2)
-- outputs 0 because of brackets
```

## Boolean Algebra

If you do not know what boolean algebra is here is a link to the [wikipedia page](https://en.wikipedia.org/wiki/Boolean_algebra), come back once you understand what boolean algebra is or just coninue if you want

Haskell has the following values and opperators for boolean algebra


|keyword/operator|function|
|----|----|
|True|true keyword in haskell (watch for capitalization)|
|False|false keyword in haskell (watch for capitalization)|
|not|inverts the Boolean value
|&&|and operator in haskell
|\|\||or opperator in haskell|
|==|equality opperator|
|/=|inequality opperator (yes it uses a forward slash instead of !, not a typo)
|>|Greater than|
|>=|Greater than or equal to|
|<|Less than
|<=|Less than or equal to|


Here are some examples of boolean algebra in haskell

```haskell
-- And operator
True && True
-- True
True && False
-- False
False && False
-- False

-- Or Opperator
True || True
-- True
True || False
-- True
False || False
-- False

-- not Opperator
not True
-- False
not False
-- True
not (True && True)
-- False

-- Equality opperator (==)
5 == 5
-- True
1 == 0
-- False
"Hello" == "Hello"
-- True

-- Inequality opperator (/=)
5 /= 5
-- False
5 /= 4
-- True

-- Greater than/Less than (same thing just inverted)
5 > 4
-- True
5 > 5
-- False
5 < 4
-- False
5 < 6
-- True

-- Greater than/Less than or equal to (once again same thing just inverted)
5 >= 4
-- True
5 >= 5
-- True
5 <= 6
-- True
5 <= 5
-- True
```

Note that in haskell you cannot mix types. For example you cannot do `5 + "hello"`.  That will result in the following error

```haskell
    • No instance for ‘Num String’ arising from the literal ‘5’
    • In the first argument of ‘(+)’, namely ‘5’
      In the expression: 5 + "hello"
      In an equation for ‘it’: it = 5 + "hello"
```

Same goes for mixing numbers and booleans, unlike lower level languages like C the `True` keyword does not equal 1, it is its own type and therefore cannot be compared with an integer.  Doing so will result in a similar error as above

You can however add floats and ints.  The only difference is even if the float is a whole number such as `9.0` haskell will still convert to a float

```haskell
9.0 + 5
-- 14.0

9.5 + 5
-- 14.5
```