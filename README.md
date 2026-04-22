# eso-esolang
Eso esoteric language online interpreter

# language tour
Eso is a stack-based esoteric language, use single-character commands to manipulate the stack and type numbers to push them into the stack

## commands
* `^` duplicates the top of stack\
* `v` pops the top of stack\
* `&` pops the top of stack, wait for a **valid** command, then push it back into the top\
* `any number literal` push number into stack
  > Eso works with integers; decimal part is not allowed

`$` pops and print the top of the stack as a Unicode character/
`#` pops and print the top of the stack as a decimal

*Work in Progress.*
