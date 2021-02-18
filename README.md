# makefile-stuffs

In this repo, I will explore `make` and `Makefile`, this is part of my learning process. I will try to add things that I have learned and also the resources. 

# Makefile

- If you want to run or update a task when certain files are updated, the make utility can come in handy. 
- The make utility requires a file, Makefile (or makefile), which defines set of tasks to be executed. 
- Run and compile your programs more efficiently with this handy automation tool. 
- Before start ensure that `make` is installed in your system.
- Makefile doesn't execute line by line code like many others, it does the whole, so you can first assign a variable to another thing and then declare that variable.

# Makefile Structure

```shell script
target: prerequisites
<TAB> recipe
```

```shell script
final_target: sub_target final_target.c
        Recipe_to_create_final_target

sub_target: sub_target.c
        Recipe_to_create_sub_target
```

# Terms Definition

* target: 
* prerequisites: 
* recipe: 
* phony targets: 
* .DEFAULT_GOAL: 
* .PHONY: 
* variables:
* patterns: 
* functions:

# Different types of operator for assigning variable value

* Recursive Expanded Variable (`=` operator):
    - we can assign a variable value by `=` operator, ex: `CC = gcc`
    - It is evaluated everytime the variable is encountered in the code.
    - when you use this be careful about the concepts about assigning another variable in a variable by `=` operator, below example will show error, cause by `=` operator it works like assign right part varible value of left part varaible.
        - ```Makefile
          CC = gcc
          CC = $(CC)
          
          check:
                @echo $(CC)
          ```
        - ```Makefile
          a = 10
          b = $(a)
          a = 20
          
          check:
                @echo "a = $(a) and b = $(b)"
          ```
          if we do `make` for this example the output will be `a = 20 and b = 20`, think about pointers, it basically works like that, here by `b = $(a)` means `b` point the `a`'s location but `b`'s value cannot change `a`'s value.

* Simply Expanded Variable (`:=` operator):
    - we can assign a variable value by `:=` operator, ex: `CC := gcc`
    - this is not like recursive-expanded-variable, so it does not have that problem
    - It is evaluated only once, at the very first occurrence
    - For example:
        - ```Makefile
          CC := gcc
          CC := $(CC)
          
          check:
                @echo $(CC)
          ```
          it won't show any error like recursive-expanded-variable, the output will be `gcc`

# `wildcard` function

- ```Makefile
  $(wildcard pattern...)
  ```
  This string, used anywhere in a makefile, is replaced by a space-separated list of names of existing files that match one of the given file name `patterns`. If no existing file name matches a pattern, then that pattern is omitted from the output of the wildcard function.

- One use of the wildcard function is to get a list of all the C source files in a directory, like this:
    - `$(wildcard *.c)`
- We can change the list of C source files into a list of object files by replacing the ‘.c’ suffix with ‘.o’ in the result, like this:
    - `$(wildcard *.o)`

# Techniques & Concepts & Basics

- only one `Makefile` should be in a folder
- only `make` will run the first target from the `Makefile` by default, first target in the makefile is the default target.
- use `make <target_name>` for running the specific <target_name> target from the `Makefile` 
- Both `${CC}` and `$(CC)` are valid reference of a variable named `CC`
- Makefile doesn't execute line by line code like many others, it does the whole, so you can first assign a variable to another thing and then declare that variable.
- always remember <TAB> while giving the recipe
- to avoid printing the command while doing `make` we need to give `@` in front of the commands, for ex: `@echo "oka"`
- `make -n <target_name>`: For seeing the process sequences by which makefile executes the all process (it will execute the sequnce from left to right), it's just preview not the execution


# Resources

- [x] [What-hos-makefile](https://opensource.com/article/18/8/what-how-makefile)
- [x] [Makefile Tuto](https://makefiletutorial.com/#static-pattern-rules)
- [x] [Understand the Makefile of this project](https://github.com/thockin/go-build-template)
- [ ] [Book](https://www.gnu.org/software/make/manual/html_node/index.html)