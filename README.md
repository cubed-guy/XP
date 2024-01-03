# XP
A golfing language with typable commands based on [05ab1e](https://github.com/Adriandmen/05AB1E).

## Introduction
XP is a stack based language. Values get pushed onto the global stack. Most operations are performed on the stack.

Literal values like numbers will get pushed onto the stack one after the other. Thus, this code
```c
40 60
```
will push 40 and then 60 onto the stack.
```c
Stack:
+----+
| 60 |  <- top
+----+
| 40 |
+----+
```

An operation like `+` pops the top two elements and pushes the result back onto the stack.
```c
40 60+
```
This will cause 100 to be on the top of the stack.
```c
Stack:
+-----+
| 100 |  <- top
+-----+
```

String literals are enclosed in double quotes.
```c
"Hello""World"
```
This pushes the string "Hello", and the "World" onto the stack.
```c
Stack:
+---------+
| "World" |  <- top
+---------+
| "Hello" |
+---------+
```

Performing `+` now will concatenate them. It's a golfing language, so a lot of things are implied.
```c
"Hello""World"+
```
```c
Stack:
+--------------+
| "HelloWorld" |  <- top
+--------------+
```

### Taking inspiration from 05ab1e
Some clever features of 05ab1e have made their way into XP.
- Looping constructs automatically begin a code block. `F <code> }` is the syntax for a `for` loop.
- The top of the stack gets implicitly printed if nothing else was printed at the execution. `"Hello, World!"` is a hello-world program.
- Ending a block / string is implied by eof. `"Hello, World!` is also a hello-world program.
- Input is also taken implicitly if the stack is empty and an operation requires arguments. `+` is a program that prints the sum of two numbers taken from the user.
