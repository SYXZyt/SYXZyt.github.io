# Instructions

## Let

The `let` keyword will update the value of a variable, or assign it if it does not exist.

```
;This will create x
let x "SPL"
let x "New Value" ;This will update the value of x
```

All variables must be created before use.

```
push x ;This will fail since x has not been created yet
let x 1
push x ;This is ok because x has already been created
```

## Setpop

`setpop` is similar to the `let` keyword, however it will take the value of the variable from the stack instead of being
given an explicit value.

```
push 3.1415
setpop pi ;pi now contains 3.1415
```

`setpop` will operate on variables that already exist and have not been defined

```
push 0
let x 0
setpop x

push 0
setpop y ;Even though y has not been defined, setpop will create it
```

## Print

Printing uses two different keywords. `print` and `println`. As you might be able to guess from the name, `println` will
print with a new line character appended at the end of the output.

```
print "Hello"
println " There "
print "World!"
;This will display this in the console:
;Hello There
;World!
```

Printing also works with all data types and variables
```
let x "Hello"
println x
print "Hello"
print 1
print 3.1415
```

## Calling

SPL uses two keywords to deal with calling. `goto` and `call` are the two main instructions used.
`goto` will jump to a set code point.
`call` does the same, except it will add to the callstack which allows you to return back to where you came from.
If you need a section of code to act like a function, you should use `call` where-as if you need a loop, then you should
use `goto`. If you use `call` without returning too much, you will get a stack-overflow error.
```
:myLoop
    println "Hello"
    goto myLoop
```
```
:myFunc
    call myFunc ;Will cause a stack-overflow error since it is not returned
```
```
:myFunc
    ;... do some processing
    ret
    
call myFunc ;Will not cause an error, since ret is used
```

## Stack Manipulation
The stack is the main method of storing data in SPL.
`push`, `pop` and `setpop` are the main methods of moving data to and from the stack.

`push` will add data onto the stack. It can take any data type, and variables.
`pop` will remove data from the stack, but will not do anything with it so the data will be deleted.
`setpop` will pop the data, but instead of deleting it, it will move it into a variable.

```
push 1
push 2
pop
setpop x
println x ;1 will be printed since 2 got popped of the stack
```

## Maths
SPL has numerous maths instructions. These will take values off of the stack, and will push
a result back onto it.
It is important to be aware that the order of pushing values is reversed from what you might expect.
The left hand side will be popped first so make sure you push the right hand side first.

## Adding
The `add` instruction will take two numeric values and push the result onto the stack.
```
push 5
push 10
add
setpop res ;res now stores 15 (10 + 5)
```

## Subtracting
The `sub` instruction will take two numeric values and push the result onto the stack
```
push 5
push 10
sub
setpop res ;res now stores 5 (10 - 5)

push 10
push 5
sub
setpop res ;res now stores -5 (5 - 10)
```

## Multiplication
The `mul` instruction will take two numeric values and push the result onto the stack
```
push 5
push 10
mul
setpop res ;res now stores 50 (10 * 5)
```

## Division
The `div` instruction will take two numeric values and push the result onto the stack
```
push 5
push 10
div
setpop res ;res now stores 2 (10 / 5)
```