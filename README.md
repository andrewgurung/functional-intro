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