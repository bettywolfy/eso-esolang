# Bolt esolang

* `<` moves a item to bottom of stack with depth based on last item of stack
  > `0 0 A 3 <` → `A 0 0`
* `.` reverses the order of the last n items of the stack with n being the last item on stack
  > `3 2 1 3 .` → `1 2 3`


### arithmetic
* `` ` `` turns the top of stack stack into its signal (either -1, 0, or 1)
* `~` turns the top of stack into 1 if it is 0, and 0 otherwise
* `+`, `-`, `/`, `*`, `%` : performs their respective operations on the last two items in the stack
  > `3 4 +` → `7`\
  > `6 2 /` → `3`


### code group
* `(...)` executes ... once; it "eats" the items stored by a `&` and wait until the last command inside itself is executed to put them back into the stack
  > `1 2 3 &(+3*)` → `9 3`
* `[...]` executes ... while there is still items on stack and the current item on top of stack is not 0


### stdout
* `$` pops and prints the top of the stack as a Unicode character
  > `65 $` → `A` (in stdout)
* `#` pops and prints the top of the stack as a decimal
* `o` prints the stack as a sequence of numbers joined by a space character
* `"..."` will print ... to the stdout


### stdin
* `?` asks for user input as a number
  > if a non-number is typed, it pushes 0 to the stack
* `!` asks for user input and then pushes every character to the stack as their codepoint, then pushes the length of input
  > if a empty string is typed, it pushes 0 to the stack


## code syntax
* `¢`: everything after this character will be ignored until the line breaks
* `'[\s\S]`: it is interpreted by the parser as a number whose value is equal to the codepoint of the character immediately after the `'`
  > `'B` → `66`\
  > `'+` → `43`


## macros
Macros are a way to repeat actions without repeating code, each macro is treated as a group `(...)`, so macros are valid operations for `&`


### defining new macros
You can define macros in the first lines of your code, before any piece of actual code\
Start by typing a `\` in your code, followed by a non-whitespace character that is not being used already, followed by a tab/space, et voilá! everything after this until the end of the you line will be the macro body
```bolt
\s ^*
3 s # ¢ 9
```
The first line defines `s` as the macro `^*`, whenever the character `s` is found in your code, `(^*)` will be executed. writing `3 (^*) #` would have the same effect.


*Work in Progress.*
