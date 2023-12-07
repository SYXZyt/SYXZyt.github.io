# Intro

SPL is a simple scripting language, which features x86 and BASIC inspired syntax. The language was created as a learning tool into interpreter design. The language features a custom made bytecode platform, which the language compiles to. As of right now, there is no JIT compilation, meaning the language could be sped up by compiling from bytecode to machine code.

The language works by pushing values onto the stack, manipulating them, then moving them into variables. This can be used to create some advanced arithmetic. The language is currently only available on Windows, however I would like to port over to Linux in the future. SPL also refers to each bit of code as an instruction, as when they are compiled, they become a single instruction on the virtual processor. SPL has finally reached v1.2, which is expected to be its end of support. Version 1.2 has implemented console manipulation, allowing programs to be more visually impressive See examples for programs that I used these features on.

SPL programs can use breakpoints, to allow an easier time debugging.

Here's a quick example
```
:loop
    println "Hello, World!" ;See how easy the syntax is =D
    goto loop
```