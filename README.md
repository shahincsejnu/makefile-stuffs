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
    - when you use this becareful about the concepts about assigning another variable in a variable by `=` operator, below example will show error, cause by `=` operator it works like assign right part varible value of left part varaible.
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


# Techniques & Concepts & Basics

- only one `Makefile` should be in a folder
- only `make` will run the first target from the `Makefile` by default, first target in the makefile is the default target.
- use `make <target_name>` for running the specific <target_name> target from the `Makefile` 
- Both `${CC}` and `$(CC)` are valid reference of a variable namded `CC`
- Makefile doesn't execute line by line code like many others, it does the whole, so you can first assign a variable to another thing and then declare that variable.
- always remember <TAB> while giving the recipe

# Resources

- [x] [What-hos-makefile](https://opensource.com/article/18/8/what-how-makefile)
- [x] [Makefile Tuto](https://makefiletutorial.com/#static-pattern-rules)
- [x] [Understand the Makefile of this project](https://github.com/thockin/go-build-template)
- [ ] [Book](https://www.gnu.org/software/make/manual/html_node/index.html)