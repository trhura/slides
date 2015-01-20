class: center, middle

# Jargons You Show Know
### Before
# Learning A New Programming Language
---
class: middle, center

# About me

---
# Agenda

+ **Language Category**
  + Strongly Typed <small>Vs</small> Weakly Typed
  + Imperative <small>Vs</small> Functional Paradigms
  + Dynamic <small>Vs</small> Static Typing
  + ........

+ **Features**
  + Closures
  + Monkey Patching
  + Meta-programming
  + ........

---
# Low Level <small>Vs</small> High Level

+ **Low Level Programming Language**
  + Little or no abstraction from a computer's instruction set architecture.
  + Either machine code or assembly language, sometime C

+ **High Level Programming Language**
  + Strong abstraction from the details of the computer.
  + The amount of abstraction provided defines how "high-level" a programming language is.

---
# Language Generation
</br>
+ **1GL** — <small>machine language</small>

+ **2GL** — <small>assembly language</small>

+ **3GL** — <small>supports structured programming, C, C++, C#, Java</small>

+ **4GL** — <small>domain-specific languages (reports, databases), blurred distinction with 3GL as they also support 4GL abilities</small>

+ **5GL** — <small> solving problems using constraints given to the program, rather than using an algorithm written by a programmer. Constraint-based and logic programming languages and declarative languages. </small>

---
# Compiled <small>Vs</small> Interpreted

+ **Compiled Language**
 + compiled source code to native code or bytecode <small>(intermediate form)</small> at compile time.
 + Machine-friendly, more efficient
 + Execution speed <small>Vs</small> Cross-platform compatibility. (<small>multiple compilation targets</small>)

+ **Interpreted Language**
  + execute instructions directly, without previously compiling a program into machine-language instructions at run time.
  + slower but easier to develop (<small>scripting, prototyping</small>)

---
# Static <small>Vs</small> Dynamic Typing

+ ** Static Typing **
 + Type checking is done at compile time. (Not declaration)
 + find type errors reliably at compile time.
 + Type Inference – haskell, golang
```Java
  int x = 3; // static typing - Java, C
  x = 3 // dynamic typing - Python, Ruby
```
+ ** Dynamic Typing **
 + Type checking is done at compile time.
 + Faster development pace, (reduce the edit-compile-test-debug cycle)

---
# Strongly Typed <small>Vs</small> Weakly Typed

+ **Strongly Typed**
 + generate an error or refuse to compile a program if incorrect type is used
 + need to explicitly cast, such as <small>`int("3")`</small>
```Java
x = "5" + 6 // => "56" in Javascript
x = "5" + 6 // => 11 in Perl, PHP
// Error in python/ruby
```

+ **Weakly Typed**
 + produce unpredictable results or may perform implicit type conversion instead.

---
# Strong/Weak <small>Vs</small> Static/Dynamic

</br>
+ **Static/Dynamic typing**
 + is about when type information is aquired (Either at compile- or at runtime)

+ **Strong/Weak typing**
 + is about how strictly types are distinguished (e.g. whether the language tries to do implicit conversion from strings to numbers).


---

# Memory Management

</br>

+ **Manual Memory Management**
 + manual instructions by the programmer to identify and deallocate unused objects
 + C, C++
 + memory leak, dangling/null pointer, segmentation faults

+ **Automatic Memory Management**
 + Garbage Collection – reclaim memory occupied by objects that are no longer in use by the program.
 + Java, C#

---
# Programming Paradigms

+ **Procedural** – structured programming, instructs a computer what to do step by step using routines. Often synonymous with imperative programming.

+ ** Object-oriented <OOP>** – based on the concept of "objects", which are data structures that contain fields (attributes) and procedures (methods).

+ **Functional** – treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

+ **Logical** –  based on formal logic, prolog.

---
# Imperative Vs Functional

```python
# add numbers from 0 ... 100
# written in imperative style with python
def sumto100 ():
    sum = 0
    i = 0
    while i <= 100:
        sum += i
        i++
    return sum
```

```lisp
(defn sumto100 []
	;; add all numbers from 0 to 1000
	(reduce + (range 101)))
```

---
# Data Types
<br/>
+ **Primitive Types**
 + basic type or builtin type
 + numbers, characters, booleans, references, string, (lists, functions)

+ **Composite Types**
 + constructed using primitive types or other composite types
 + for example – struct

---
# Scope (Visibility/Lifetime)

+ the part of a computer program where the name binding is valid.

 + **Lexical Scoping**
     + depends upon the lexical context (source code)
     + compile time, early binding

 + **Dynamic Scoping**
	 + depends on the program state when the name is encountered
	 + run time, late binding

---

# Scope (Example)

+ From http://stackoverflow.com/a/22395580

```Java
program a() {
  x: integer; // "x1" in discussions below
  x = 1;

  procedure b() {
      x = 2; // <-- which "x" do we write to?
  }
  procedure c() {
      x: integer; // "x2" in discussions below
	  b();
  }

  c();
  b();
}
```

---
# Naming Conventions

<br/>

+ **snake_case** – words are separated by underscore

+ **CamelCase** – each words begin with a capital letter

+ **Hungarian Notation** –  the name of a variable or function indicates its type or intended use.

+ **Sigils** – indicate dataype or scope, similar to above but declare the type of the variable to the compiler.

```python
bBusy = true # b for Boolean
$globalvar, @instancevar, @@classvar, ?, ! # ruby
```
---

## First Class Functions
 + first-class functions if it treats functions as first-class citizens.
 + passing functions as arguments to other functions, returning them as values and assigning them to variables or storing them in data structures.

## High-order functions
 + a function taking another function as argument is called a higher-order function
```lisp
(map + (list 0 1 2)) => (1 2 3)
```

---

# Closures
 + functions with references to non-local variables

```javascript
// from http://www.w3schools.com/js/js_function_closures.asp
var counter = 0;
function add() {
	counter += 1;
}

function add() {
    var counter = 0;
	counter += 1;
}

var add = (function () {
    var counter = 0;
	return function () {return counter += 1;}
})();

```

---
# Functions

## Anonymous Functions
 +  a function definition that is not bound to an identifier.
```lisp
(map (fn [x] (+ x 2)) (list 1 2 3)) => (3 4 5)
```

## Coroutines/Continuations
 + allowing multiple entry points for suspending and resuming execution
 + the ability to save the execution state at any point and return to that point later, possibly multiple times

---
## Pattern Matching

+ Conditional programming construct
```haskell
factorial 0 = 1
factorial n = n * factorial (n-1)
```

## Lazy Evaluation
+  Delays the evaluation of an expression until its value is needed
```clojure
(defn fib []
	(let [lazy-fib (fn lazy-fib [a b]
						(cons a (lazy-seq (lazy-fib b (+' b a)))))]
		(lazy-fib 1 2)))
(take 10 (fib)) ;; (1 2 3 5 8 13 21 34 55 89)
```
---
## String Interpolation
+ string literal containing one or more placeholders
```ruby
apples = 4
puts "I have #{apples} apples"
```

## Monkeypatching

+ Dynamic modifications of a class or module at runtime
+ Patch existing third-party code as a workaround to a bug or feature which does not act as desire
+ Distribute security or behavioural fixes that live alongside the original source code (Ruby on Rails).

---
# Metaprogramming

+ The ability to treat programs as their data
+ a program that can read/generate/transform other programs, or even modify itself while running.

  + **Reflection** – the ability of a computer program to examine (see type introspection) and modify the structure and behavior of the program at runtime.

  + **Homoiconicity** –  a program's source code is written as a basic data structure that the programming language knows how to access.

---
# Libraries <small>&</small> Repositories

+ **Standard Library**
  + the library made available across all implementations
  + includes commonly used algorithms, data structures, classes and other constructs

+ **Software repository**
  + CPAN, NPM

+ **Package Manager**
  + pip, gems ..

---
# License

+ **Proprietary**
 + the right to use the software only under certain conditions, and restricted from other uses, such as modification, sharing, studying, redistribution, or reverse engineering.

+ **Open-Source**
 + the source code is available to the general public for use and/or modification

 + **Permissive** – MIT, BSD, APACHE
 + **Copyleft** – GPL, LGPL, AGPL

---
class: center, middle

# <big>Thanks !</big>
### trhura@gmail.com
### fb/thurahlaing
### github/trhura
### linkedin/trhura
