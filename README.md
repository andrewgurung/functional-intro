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
-----------

## Types and Classes

-----------

## Defining Functions

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

-----------

## Declaring Types and Classes

-----------

## The Countdown Problem

-----------

## Lazy Evaluation

-----------


## Reasoning about Programs

-----------