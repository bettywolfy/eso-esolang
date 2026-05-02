# eso-esolang
Eso esoteric language online interpreter

# language tour
Eso is a stack-based esoteric language, use single-character commands to manipulate the stack and type numbers to push them into the stack

## commands

### create value
* `@` push into stack a 0 or 1 randomly
* `?` ask for user input as a number
* `!` ask for user input and push into the stack every character as int codepoint, then push the length of input
* `[0-9]+` push the number value into stack
  > integer only; use `n 0:-` for negative values

### stack manipulation
* `^` duplicates the top of stack
* `v` pops the top of stack
* `&` pops the top of stack, wait for a **valid** command to be executed and then push the stored items back into the top
  > `&`, `[...]`, `o` and pushing a number into stack are not valid commands\
  > `&` can be stacked: `0 2 3 &&1+` → `1 2 3`
* `:` flip the last 2 items on stack
* `;` swap 2 items on stack with depth based on the last 2 items of stack
  > `A B 0 0 4 3 ;` → `B A 0 0`
* `>` move a item to top of stack with depth based on last item of stack
  > `A 0 0 3 >` → `0 0 A`
* `<` move a item to bottom of stack with depth based on last item of stack
  > `0 0 A 3 <` → `A 0 0`
* `.` reverse the order of the last n items of the stack with n being the last item on stack

### arithmetic
* `|` turn the top of stack stack into its absolute value
* `~` turn the top of stack into 1 if it is 0, 0 otherwise
* `+`, `-`, `/`, `*`, `%` do the operation to the last 2 items on stack
  > `3 4 +` → `7`\
  > `6 2 /` → `3`

### code group
* `(...)` execute once; if a `&` is used before, it "eats" the items stored until the last command is executed
  > `1 2 3 &(+3*)` → `9 3`
* `[...]` execute while there is still items on stack and the current item on top of stack is not 0

### stdout
* `$` pops and prints the top of the stack as a Unicode character
* `#` pops and prints the top of the stack as a decimal
* `o` prints the stack as a sequence of numbers joined by a space character

*Work in Progress.*
