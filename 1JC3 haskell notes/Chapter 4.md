# Chapter 4 - Data Types, Variables, and Lists

## Data Types

In haskell we have a variety of types builtin.  Here we are going to go over the most basic types

### Int

An `Int` is a whole number with a fixed size.  It is a signed number meaning it can be positive or negative value.  This is used when you don't have an obscenely large number.  You should try to use this when you can as it is faster than its counterparts for arithmetic. it has variations of `Int8` for 8 bit signed numbers, `Int16` for 16 bit signed number, `Int32` for 32 bit signed numbers and `Int64` for 64 bit signed numbers.

### Integer

An `Integer` is the same as an `Int` with one key differerence, it is not a fixed size and is only bound by the amount of ram in your system.  With that there is a caveat which is that it is slower for arithmetic than `Int` due to it's dynamic size.  The biggest advantage to `Integer` over `Int` is that `Integer` cannot overflow while `Int` can.

### Float

A `Float` is a decimal number with single precision meaning it is bound to 32-bits so it offers 6-7 digits on each side of the decimal

### Double

A `Double` is the same as a `Float` but with double precision offering 15-16 decimals on each side and takes up 64 bits

### Bool

A `Bool` is a type that have 2 values, `True` or `False`

### Char

A `Char` is a single unicode character

### String

A `String` is not a real type to the computer but should definetly be mentioned here as it is very commonly used.  A `String` simply put is a list, also known as an array, of `Char`s.  So really when you have the string `"Hello World"` all it is is `['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd']`.  Note that even the space is its own character.  We will take a look at arrays later in the Chapter

## Variables

Variables are probably going to be one of, if not the most, important and useful tools in your haskell toolbox.  Put simply a variable is a way to store temperary information only while your program is running however are very fast at accessing.

In haskell variables do not exist in your traditional sense, instead they are immutable (cannot change value after creation) and are instead known as bindings.  

### Global Variables

For a global variable, which is a variable that can be accessed from any function in the same file, they are defined as such and called from functions like so.

```haskell
-- creating global variable x and setting it to 5
x :: Int
x = 5

-- creating function multiply x

multiplyX :: Int -> Int
multiplyX y = x * y
```

So you will notice that the declaration of x and creation of the function multiplyX use similar syntax, this is not an error, this is because in haskell **everything is a binding**.  So what is a binding?  A binding put simply is a name, associated with a value or expression.  So in this example:

- `x` is bound to the fixed value of 5
- `multiplyX` is bound to an expression that takes in a parameter `y` and multiplies the two.  This is called a function binding.  So as an example if `y` is `3`, multiplyX would evaluate to `15`

A binding can be either a direct value `x = 5` or an expression `multiplyX y = x * y`.

### Local Variables

Local variables, are variables that can only be used in a specific block of code, whether this is inside a function or even a section of a function.  Parameters are local variables along with the following methods of defining them below.

In haskell we use the `let` and `in` keywords for local variables.  The following is an example of using local variables.

```haskell
addFiveAndDouble :: Int -> Int
addFiveAndDouble x =
    let 
        y = x + 5
    in 
        y * 2
```

So what is even going on here?  Well at this point you should know the notation at the top, we are defining a function called addFiveAndDouble that takes in variable `x`.  **From this point on when there is a function, we will not explain this part and assume you understand this syntax.**  We then create a new variable y with the `let` keyword which takes in `x` and adds `5`.  We then have the in keyword which then takes y and multiplies it by 2 and because that is the last line, that is what the output of the function is.  The `in` keyword is there because we can only use y within the `in` keyword.  If we unindent after the in, we exit it and the y binding is no longer accessible to us.  When using `let` and `in` you can define multiple variables and have multiple lines using them, below is an example of this.

```haskell
areaBiggerThanPerimeter :: Int -> Int -> String
areaBiggerThanPerimeter x y =
    let
        area = x * y
        perimeter = 2 * (x + y)
    in
        if area > perimeter then "Area"
        else if perimeter > area then "Perimeter"
        else "Equal"
```

This function checks if the area is larger than the perimeter and outputs as a string which is larger and shows how you can define multiple variables within one `let`, and have multiple lines in the `in`.

What you have just seen is something called the scope where global variables are in the global scope and the variables in the let, in are in the local scope for those keywords.

There is another way to define local variables which is with the `where` keyword.  An example of the `areaBiggerThanPerimeter` function, rewritten using `where` can be found below.

```haskell
areaBiggerThanPerimeter :: Int -> Int -> String
areaBiggerThanPerimeter x y = output
    where
        area = x * y
        perimeter = 2 * (x + y)

        output = if area > perimeter then"Area"
            else if perimeter > area then "Perimeter"
            else "Equal"
```

So one major difference than the let is that we are defining the output of the function as a variable at the top of the function which we are calling `output`.  Below it we have the actual logic.  Once again we are defining area and perimeter however this time we are setting `output` to be equal to the result of the if statement.

These are the basic ways of declaring local variables, there are others however this is beyond the scope of this chapter.

## Lists

### Creating a list

Lists are simply a list of multiple values.  Here is how we define a list.

```haskell
myList = [1, 3, 5, 7]
```

When we call myList it outputs `[1, 3, 5, 7]`

You can also combine 2 lists with the `++` opperator

```haskell
myList = [1, 2] ++ [3, 4]
```

which will output `[1, 2, 3, 4]`

### Accessing a list

You saw before how to access a list as a whole but how about individual values?  If you want to access an individual value you can use the `!!` opperator.  **Note that Haskell starts at 0 so the first element in the list is index 0**

```haskell
myList = [1, 2, 3, 4]
myList !! 2
-- 3
```

Here are some other ways you can access and get information about a list.

```haskell
let myList = [1, 5, 2, 4, 9]

-- we have our original way which is by index
myList !! 2
-- 2

-- using the head keyword will get you the first element, same as !! 0
head myList
-- 1

-- using the last keyword will get the last element
last myList
-- 9

-- the init keyword gives you every element but the last
init myList
-- [1, 5, 2, 4]

-- the tail keyword gives you every element but the first
tail myList
-- [5, 2, 4, 9]

-- the length keyword gives us how many elements are in the list
length myList
-- 5

-- the null keyword tells us if a list is empty and ouputs as a True or False boolean value
null myList
-- False

-- the reverse keyword reverses the order of the elments in the list
reverse myList
-- [9, 4, 2, 5, 1]

-- the take keyword takes a number and a list and ouputs the first n number of elements in the list
take 3 myList
-- [1, 5, 2]

-- the drop keyword takes a number and a list and removes (or drops) the first n number of elements in the list
drop 3 myList
-- [4, 9]

-- the maximum keyword outputs the largest number in a list, minimum does the same but for the smallest number
maximum myList
-- 9
minimum myList
-- 1

-- the sum keyword takes the sum of all the elements in the list and the product does the same but for the product (muliplication)
sum myList
-- 21
product myList
-- 360

-- the elem keyword checks if an item exists in a list, recommended to be called as an infix function
9 `elem` myList
-- True
20 `elem` myList
-- False
```

If you cannot memorise these right now that is completely fine, you will become more and more familiar with them the more you use them and eventually will be second nature.  If you need to remember them, you can always refer to this guide.

### Comparing Lists

you can also compare lists using equality symbols such as `>`, `<=`, `==` etc.  They will start at the first value and move down the list.  Let's do an example with the `>` opperator.

```haskell
[1, 2, 4] > [1, 2, 3]
-- True

[1, 2, 3] > [1, 2, 4]
-- False
```

Note that an empty list is always greater than a non-empty list.

### Convenient ways of creating lists

Let's say you want to create a list between 1 and 20.  You may expect you would need to type all those out manually, but that is not the case.  Haskell has some special notation you can use.  To create a list between 1 and 20 you can simply do `[1..20]` and that will creat a list that looks like `[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]`.  You can do the same with characters so ['b'..'f'] will make `"bcdef"`.  Wait why did it create a string.  Well Haskell did exactly what we told it to do.  It created an arry of characters and as mentioned before an array of characters is just a string.  This means all the functions we had before can actually be used on a string so

```haskell
'h' `elem` "hello world"
-- True
```

Moving back to creating lists, that notation also works for capitals so ['B'..'F'] will create `"BCDEF"`.

It also can work with intervals but is limited so something like [2, 4..20] will create `[2,4,6,8,10,12,14,16,18,20]` however trying to do powers of 2 like `[2, 4, 8, 16..32]` will throw an error.

If you want to create a list in order of 20 to 1 you cannot just do `[20..1]`, you must do `[20, 19..1]`.

Haskell can also allow you to create "infinite" lists.  If you use the notation `[2, 4..]` it will create a list of every even number.

You can use the `take` keyword to only take a specific number of elements from the created list so if you do `take 24 [2, 4..]` it will create the first 24 even numbers being between 2-48.

### List Comprehensions

List comprehensions allow you to filter, transform and combine lists.

Let's look at an eample

```haskell
[x^2 | x <- [2, 4..10]]
-- [4,16,36,64,100]
```

Let's look at this from right to left

1. **Input List:** `[2, 4..10]` we create an input list of every other element
2. **Generator:** `x <-` takes each element and assigns it to x
3. **Output Expression:** `x^2` for each x, square it and add it to the output list

The `|` separates the output expression from the generator

so step by step it looks like

1. create a list of [2, 4, 6, 8, 10]
2. Take `x = 2` -> `x^2 = 4`
3. Take `x = 4` -> `x^2 = 16`
4. Take `x = 6` -> `x^2 = 36`

We can make these even more complicated.  What if we only want values where `x*2 >= 10`.  We can write

```haskell
[x^2 | x <- [2, 4..10], x*2 >= 10]
-- [36,64,100]
```

Note that the check happens before the **Output Expression**.

How about we create a list where every number that is divisible by 3 with no remainder gives us the string `"YAY"` and numbers that aren't give us `"NAY"` between 1 and 30

```haskell
[if x `mod` 3 == 0 then "YAY" else "NAY" | x <- [1..30]]
-- ["NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY","NAY","NAY","YAY"]
```

So what is going on here.

1. Generate numbers 1-30
2. Go through the input list with each value set to x
3. check if x / 3 has a remainder of zero and if it does add `"YAY"` to the output list, otherwise `"NAY"`
4. output the output list

You can also create these expressions as functions where instead of setting the list you can pass it in as a parameter

```haskell
yayNay :: [Int] -> [String]
yayNay myList = [if x `mod` 3 == 0 then "YAY" else "NAY" | x <- myList]
```

Here we are passing in a list to a function instead of hardcoding it.

you can also have multiple variables as input lists

```haskell
[x * y | x <- [1..3], y <- [2..4]]
-- [2,3,4,4,6,8,6,9,12]
```

when you do this every combination of the expression is created so the expression will do:

`1 * 2 = 2`

`1 * 3 = 3`

`1 * 4 = 4`

`2 * 2 = 4`

`2 * 3 = 6`

and this continues 9 times because there are 3 elements in each list and `3*3=9`