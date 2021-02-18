# makefile-stuffs

In this repo, I will explore `make` and `Makefile`, this is part of my learning process. I will try to add things that I have learned and also the resources. 

# Makefile

- If you want to run or update a task when certain files are updated, the make utility can come in handy. 
- The make utility requires a file, Makefile (or makefile), which defines set of tasks to be executed. 
- Run and compile your programs more efficiently with this handy automation tool. 
- Before start ensure that `make` is installed in your system.

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



# Techniques & Concepts & Basics

- only one `Makefile` should be in a folder
- only `make` will run the first target from the `Makefile` by default, first target in the makefile is the default target.
- use `make <target_name>` for running the specific <target_name> target from the `Makefile` 
- Both `${CC}` and `$(CC)` are valid reference of a variable namded `CC`

# Resources

- [x] [What-hos-makefile](https://opensource.com/article/18/8/what-how-makefile)
- [x] [Makefile Tuto](https://makefiletutorial.com/#static-pattern-rules)
- [x] [Understand the Makefile of this project](https://github.com/thockin/go-build-template)
- [ ] [Book](https://www.gnu.org/software/make/manual/html_node/index.html)