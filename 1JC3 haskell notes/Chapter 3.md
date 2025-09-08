# Chapter 3 - Conditionals

## if/else/then

In Haskell `if` is an expression that evaluates to a value. An if expression must include both then and else. The expression after then and the expression after else must have the same type.

```haskell
signOf :: Int -> String
signOf x = 
    if x > 0 then "Positive"
    else if x < 0 then "Negative"
    else "Zero"
```

Ok so let's go over this whole function in detail line by line.

1. First we defined our types so it will only accept the type `Int` for the value we will be check `x` and `String` as the output type
2. We define the function signOf that takes in parameter `x`
3. We check if `x` is greater than `0` and, if it is, we then output `"Positive"`. All `if` and `else if` (which are just if statements if the previous if does not evaluate to True) expressions require a then keyword for what happens when the condition is `True`, and an else keyword for what happens when the condition is False.
4. We use else if which only happens if the previous if expression is false and if it is we output `"Negative"`
5. If neither of the previous 2 cases are true the program falls back to the else expression and will output `"Zero"` note that `else` does not need a then keyword

## Nesting If Expressions

Nesting `if` expressions means placing an `if` expression inside another `if` expression.  The inner `if` is only evaluated if the outer `if` evaluates to `True`

Below is an example of syntax for nested `if` expressions.

```haskell
if 3 > 2 then
        if 3 > 4 then
            1
        else 2
else
    3
```

Let's go over this syntax and find what the result of this will be

1. we check if `3 > 2` which is True so we move on to the nested if
2. we check if `3 > 4` which evaluates to `False` so we take the else inside the first `if` so the output of this block of code is 2
3. since we already have evaluated the first `if` to be true the outside else is ignored

While this syntax is technically correct and does work it is not good code and is only used as a basic example.  A better approach to this specific problem would be the following code

```haskell
if (3 > 2) && (3 > 4) then 1
else if (3 > 2) && (3 <= 4) then 2
else 3
```

In this the same value of 2 is reached since while 3 is greater than 2, 3 is not greater than 4 so we move to the next else if where 3 is greater than 2 and 3 is greater than or equal to 4 and since both of these are true the program outputs 2 and does not reach the else