# eso-esolang
Eso esoteric language online interpreter

Eso is a stack-based esoteric language, use single-character commands to manipulate the stack and type numbers to push them into the stack

## commands

### stack manipulation
* `[0-9]+` push the number value into stack
  > `123`, `3`, `54` (integers only)\
  > use `0:-` to negate the top of the stack
* `@` push into the stack a 0 or 1, choosing randomly
* `^` duplicates the top of stack
  > `3 ^` → `3 3`
* `v` pops the top of stack
  > `3 3 v` → `3`
* `&` pops the top of stack, wait for a **valid** command to be executed and then push the stored items back into the top
  > `1 4 &3*` → `3 4`\
  > `&` itself, `[...]`, `"..."`, `o` and `[0-9]+` are not valid commands\
  > `&` can be stacked: `0 2 3 &&1+` → `1 2 3`
* `:` flip the last 2 items on stack
  > `4 5 :` → `5 4`
* `;` swap 2 items on stack with depth based on the last 2 items of stack
  > `A B 0 0 4 3 ;` → `B A 0 0`
* `>` move a item to top of stack with depth based on last item of stack
  > `A 0 0 3 >` → `0 0 A`
* `<` move a item to bottom of stack with depth based on last item of stack
  > `0 0 A 3 <` → `A 0 0`
* `.` reverse the order of the last n items of the stack with n being the last item on stack
  > `3 2 1 3 .` → `1 2 3`

### arithmetic
* `` ` `` turn the top of stack stack into its signal (either -1, 0, or 1)
* `~` turn the top of stack into 1 if it is 0, and 0 otherwise
* `+`, `-`, `/`, `*`, `%` : performs their respective operations on the last two items in the stack
  > `3 4 +` → `7`\
  > `6 2 /` → `3`

### code group
* `(...)` execute ... once; it "eats" the items stored by a `&` and wait until the last command inside itself is executed to put them back into the stack
  > `1 2 3 &(+3*)` → `9 3`
* `[...]` execute ... while there is still items on stack and the current item on top of stack is not 0

### stdout
* `$` pops and prints the top of the stack as a Unicode character
  > `65 $` → `A` (in stdout)
* `#` pops and prints the top of the stack as a decimal
* `o` prints the stack as a sequence of numbers joined by a space character
* `"..."` will print ... to the stdout

### stdin
* `?` ask for user input as a number
  > if a non-number is typed, it pushes 0 to the stack
* `!` ask for user input and then pushes every character to the stack as their codepoint, then pushes the length of input
  > if a empty string is typed, it pushes 0 to the stack

*Work in Progress.*
