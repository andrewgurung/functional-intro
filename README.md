# Functional Intro
Introduction to Functional Programming

Author Info
-----------
Author: Andrew Gurung <br>
URL: http://www.andrewgurung.com/

-----------

## Introduction
- [Free Haskell Book](http://learnyouahaskell.com/)
- FP provides an elegant framework to write code at a high level of abstraction
- FP in a purist way is a language where you program using mathematical functions

Traditional imperative Java way:
```
int total = 0;
for (int i = 1, i <= 10; i++) {
    total = total + i;
}
```

Haskell solution:
```
sum [1..10]
```

### Installation
- [Haskell Download](https://www.haskell.org/platform/)
- Run installer which comes with a Haskell compiler (Glasgow Haskell Compiler/GHC)
- Open terminal
    - Type `ghci`
    - You will be greeted with
        ```
        GHCi, version 8.2.1: http://www.haskell.org/ghc/  :? for help
        Prelude>
        ```
    - To change prompt from Prelude to something shorter
        ```
        :set prompt "ghci> "
        ```
    - Try some arithmetic
    ```
    ghci> 2 + 15  
    17
    ``` 

### Basic Syntax
- GHC installer pack includes some basic libraries for list manipulation
    - Eg: head, tail
```
1. Add two numbers:
ghci> 2 + 15
17

2. Select the first element from a list:
ghci> head [1,2,3,4]
1

3. Remove the first element from a list:
ghci> tail [1,2,3,4]
[2,3,4]

4. Select the nth element of a list:
ghci> [1,2,3,4,5] !! 2
3

5. Select the first n elements of a list:
ghci> take 2 [1,2,3,4,5]
[1,2]

6.Remove the first n elements of a list:
ghci> drop 2 [1,2,3,4,5]
[3,4,5]

7. Calculate the sum and product of a list:
ghci> sum [1,2,3,4,5]
15
ghci> product [1,2,3,4,5]
120

8. Append two lists:
ghci> [1,2,3] ++ [4,5]
[1,2,3,4,5]

9. Reverse a list:
ghci> reverse [1,2,3,4,5]
[5,4,3,2,1]
```

### Function Application
- Mathematics:
    - Parentheses is used to denote Function
    - Space is reserved for Multiplication which is most often used in Mathematics
    - `f(a, b) + c d`
- Haskell:
    - Asterisk is used to denote multiplication
    - Space is reserved for Functions which is most common in Haskell
    - `f a b + c*d`
- f a + b
    - Means (f a) + b, rather than f (a + b)
- Converting Mathematics to Haskell
    - f(x, g(y)) ==> f x (g y)
    - f(x)g(y) ==> f x * g y

### Haskell Scripts
- In Haskell, programs are called scripts as they tend to be shorter
- New functions are defined within a script, a text file ususally having a `.hs` suffix

### My First Script
- Save the following two function definitions in `test.hs` file
```
double x = x + x
quadruple x = double (double x)
```
- Open file using GHCi in your terminal window
```
% ghci test.hs
```
- Run the loaded functions
```
> quadruple 10
40
```

### Syntactic sugar
- Use backtick for converting a function into infix operator
```
x `f` y 
equals to f x y
```

- Finding average
```
average ns = sum ns `div` length ns
```

### Useful GHCi commands
```
:reload     [reloads current script]
:load name  [load script name]
:edit       [edit current script]
:type expr  [show type of expr]
:?          [show all commands]
:quit       [quit GHCi]
```

### Naming requirement
- Functions and arguments must begin with lowercase. Eg: myFun, fun1, arg_2
- List arguments usually have `s` suffix. Eg: xs, ns, nss (list of lists)

### Layout Rule
- Whitespace is important in Haskell

-----------

## Types and Classes
- Type is a name for a collection of related values
- Type Error: `1 + False`
- Checking type of an expression
```
ghci> :type False
False :: Bool

ghci> :type [False, True, False]
[False, True, False] :: [Bool]

ghci> :type [[False, True],[True]]
[[False, True],[True]] :: [[Bool]]  ==> List of lists
```
- `e :: t` => expression has type t
- Basic Types in Haskell
    - Bool, Char, String, Int(fixed-precision integers), Integer(arbitary-precision integers), Float
- Tuple: Sequence of values of different types
```
ghci> :type ('a', False)
('a', False) :: (Char, Bool)
```

### Function type
- A function is a mapping from values of one type t1 to another type t2 denoted as `t1 -> t2`
```
add :: (Int, Int) -> Int
```

### Curried Functions
- Functions that take their arguments one at time are called curried functions
- Any function with more than two arguments can be curried by returning nested functions
- Curried functions are flexible because of partially applied functions
- Unless tuple is required, all functions in Haskell are curried

- add' is a curried function that takes an integer which returns a function that also takes an integer as argument and returns an integer
```
add' :: Int -> (Int -> Int)

Can also be written without paranthesis where arrow associates to the right.

add' :: Int -> Int -> Int
```

- add' can be written using tuples which is `not` a curried version
```
add :: (Int, Int) -> Int
```
- Function is applied in the left direction
```
mult x y z
((mult x)y)z
```

### Polymorphic Functions
- A function is called `polymorphic` if its type contains one or more `type variables`
- In the following example, 
    - `Int`: Starts with upper case and known as a type
    - `a`: Starts with lower case and is known as type variable
```
length :: [a] -> Int

ghci> length [True, False, True]
3
ghci> length [1, 2, 3, 4]
4
```
- Here `a` can be of any type. The polymorphic function `length` will take any list of String, Integer, Boolean etc and returns an integer

### Overloaded functions
- A polymorphic function is called overloaded if its type contains one or more restrictions
- Here the restriction is a has to be of Numeric type denoted by =>
- The restriction is to only allow adding numbers
```
sum :: Num a => [a] -> a

// a = Int
ghci> sum [1, 2, 3, 4]
10

// a = Float
ghci> sum [1.1, 2.2, 3.3, 4.4]
11.0

// Char is not a Num type
ghci> sum ['a', 'b', 'c']
ERROR
```

-----------

## Defining Functions

### Conditional Expressions
- Functions can be defined using conditional expressions
- if then else
```
signum :: Int -> Int
signum n = if n < 0 then -1 else
              if n == 0 then 0 else 1
```

### Guarded Equations
- Alternative to conditionals
- Syntax function | condition = result
- `otherwise` is a catch all condition
```
signum n | n < 0 = -1
         | n == 0 = 0
         | otherwise = 1
```

### Pattern Matching
- Functions can be defined using pattern matching on their arguments
- Note: Patterns do not repeat variables
- `_` is a wildcard
```
True && b = b
False && _ = False

b && b = b // Error pattern repeat
```

### List Patterns
- Every non-empty list is constructed by using cons operator (:) that concats element to form a list
```
[1,2,3,4]
// can be written as 
1:(2:(3:(4:[])))
```

- Functions on list can be defined using `x:xs` pattern
    - x:xs pattern only matches non-empty list
```
head (x:_) = x
tail (_:xs) = xs
```

### Lambda Expressions
- Lambda expressions are used to construct functions without the need of function names

- Currying
    - add x y = x + y
```
add = \x -> (\y -> x+y)
```

- Avoid naming functions that are only referenced once
```
odds n = map f [0..n-1]
         where
            f x = x*2 + 1
```
Using lambda expressions
```
odds n = map (\x -> x*2 + 1) [0..n]
```

### Sections
- A shorter way of defining functions
- Eg: Operators can be written using parentheses
```
> 1 + 2
3

> (1+) 2
3

> (+2) 2
3

> (/2) 4
2
```
-----------

## List Comprehensions

-----------

## Recursive Functions

-----------

## Higher-Order Functions

-----------

## Functional Parsers and Monads

-----------

## Interactive Programs
- Pure functions could be an overkill for task like readLine()
- So we mix imperative code with pure functions together
- Think of pure functions as islands in a sea of impure imperative code
-----------

## Declaring Types and Classes

-----------

## The Countdown Problem

-----------

## Lazy Evaluation

-----------


## Reasoning about Programs

-----------