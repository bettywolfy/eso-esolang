# eso-esolang
Eso esoteric language online interpreter

# language tour
Eso is a stack-based esoteric language, use single-character commands to manipulate the stack and type numbers to push them into the stack

## commands

### stack manipulation
* `^` duplicates the top of stack
* `v` pops the top of stack
* `&` pops the top of stack, wait for a **valid** command, then push it back into the top
* `$` pops and print the top of the stack as a Unicode character
* `#` pops and print the top of the stack as a decimal
* `:` flip the last 2 items on stack
* `;` swap 2 items on stack with depth based on the last 2 items of stack
* `>` move a item to top of stack with depth based on last item of stack
* `<` move a item to bottom of stack with depth based on last item of stack

### arithmetic
* `|` turn the top of stack stack into its absolute value
* `~` turn the top of stack into 1 if it is 0, 0 otherwise
* `+`, `-`, `/`, `*`, `%` do the operation to the last 2 items on stack

### create value
* `@` push into stack a 0 or 1 randomly
* `.` reverse the order of the last n items of the stack with n being the last item on stack
* `?` ask for user input as a number
* `!` ask for user input and push into the stack every character as int codepoint, then push the length of input
* `[0-9]+` push the number value into stack
  > integer only; use `n 0:-` for negative values

### code group
* `(...)` execute once; if a `&` is used before, it "eats" the items stored until the last command is executed
* `[...]` execute while there is still items on stack and the current item on top of stack is not 0

## examples

*Work in Progress.*
