# Walkthrough

This guide will assume that you have correctly installed or compiled SPL.

## Console
The very first thing to teach is printing text to the console. SPL features two instructions for printing. println and print As you can probably guess, one of these will add a new line character on the end of the text
```
	print "Hello, "
	println "World!"
	;Prints `Hello, World!` to the console
```
## Variables

SPL supports variables. Variables are just a value in memory. Variables can either be mutable or constant. Mutable variables means that their value can be changed, whereas constant, means the value cannot be changed once set.
```
	let x "Value" ;Note that if this was const, an error would be thrown as constant values cannot be changed
	let x "Another value"
	const PI 3.1415 ;I am constant, therefore my value must be set at compile time and cannot be changed
```
Variables can also be deleted using the free keyword.
```
	let i 0
	free i
	push i ;This will cause an error since i no longer exists on the variable stack
```

## Variable Types
SPL currently supports 3 different variable types.<br/>
The first is integers. These are numbers which contain no decimal value. <br/>
Second is floating point numbers. These are numbers which contain a decimal value <br/>
Lastly is strings. Strings are sequences of characters, although note that SPL contains no char type, and you cannot read a certain value from strings.

Variables in SPL are dynamically typed which means their value will be determined at run-time and the variable type can be re-assigned by writing a new value to a variable.
## Stack

SPL features a stack where you can move values onto. This is mostly used to simulate function parameters, or for maths operations.

You can use push or pop to add or remove values.
```
	push 2
	push 1000
	div
	setpop res
	print "1000 / 2 is "
	println res
```
## Looping

SPL can also move around the current execution. There are two ways of doing this. call will take a label name and jump to it. It also adds to the callstack, meaning you can return using the ret keyword.goto will jump without touching the callstack. By using goto, you don't just need a label name, but you can also jump to a line number
```
	println "Hello"
	goto 1
```
Using labels, we can do it this way
```
:loop
	println "Hello"
	goto loop
```
Be careful though, using call, it will add to the callstack, like a function call, meaning this code will create a stack overflow error.
```
:loop
	println "Hello"
	call loop ;This will throw an stack overflow
```

Using ret allows us to jump back to a previous location. If you return when there is nowhere to return to, then an error will throw
```
	call loop

:loop
	println "Hello"
	ret ;This will only execute once, as we are returning out of this call
	goto loop 
```