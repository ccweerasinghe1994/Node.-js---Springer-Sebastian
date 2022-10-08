# [🏠 Home Page](../../readme.md)

# 3 Developing Your First Application


By the time you get here, you should already have a working
installation of the Node.js platform on your system. To run the
examples in this chapter, you must use the command line of your
operating system. It doesn’t matter whether you use Windows, Linux,
or macOS. The examples work independently of the operating
system. You can use Node.js in two different ways. For simple
experiments, you can use the interactive shell. Alternatively, you can
run an application by passing the name of the initial file to the node
command. In this case, no further user interaction is usually
required.

## 3.1 Interactive Mode

You can reach the interactive mode of Node.js, as you can see in
`Listing 3.1`, by entering the node command in the command line.

**Listing 3.1**

```bash
➜  Node. js - Springer, Sebastian git:(master) node
Welcome to Node.js v16.14.0.
Type ".help" for more information.
> 
```

In interactive mode, you can directly enter JavaScript code on the
command line and execute it. This type of user interface is referred
to as read-eval-print loop (REPL), which means that commands are
read on the command line and evaluated, and then the result is
output on the command line. The mode isn’t intended to implement
and run complete applications. Instead, this interface of Node.js is
used to test the behavior and functionality of individual code
snippets. Figure 3.1 shows how the interactive mode works.


![Figure 3.1 Interactive Mode of Node.js](./../img/03_001.png)

### 3.1.1 General Use
Listing 3.2 shows how you can issue commands in the Node.js
REPL.

**Listing 3.2 Executing Commands in the Node.js REPL**

```bash
➜  Node. js - Springer, Sebastian git:(master) node
Welcome to Node.js v16.14.0.
Type ".help" for more information.
> console.log("hello world")
hello world
undefined
```

The JavaScript commands also end with a semicolon in the Node.js
REPL. A line break ends the input of the current command and
sends the command to the JavaScript engine. In the example, the
`console.log` method with the `Hello World!` argument is evaluated,
and the `Hello World!` result is output to the command line. As you
can see in Listing 3.2, the value `undefined` is output in addition to the
expected `Hello World!`. This is because the return value of the
console.log function is represented; in this case, it’s `undefined`.
Apart from executing output, in REPL, you can also execute all
JavaScript commands available under Node.js, as shown in
Listing 3.3

**Listing 3.3 Definition of a Simple Node.js REPL Function**

```bash
> function greet(name) {
... console.log(`Hello ${name}`);
... }; greet('world');
Hello world
undefined
>
```

`Listing 3.3` shows how to define a function in Node.js REPL that gets
a name as a parameter and how to output it to the console as the
function progresses. After the definition, the function `greet` is called
with the argument `world` as name. The output consists of `Hello world`
and `undefined`. If you want to run different commands in the Node.js
REPL that build on each other, you can easily do so because the
context is preserved within a session. For example, if you define
functions or perform a variable assignment, these will be preserved
even after the command line is evaluated. In Listing 3.4, you can see
how this works in concrete terms.

**Listing 3.4 Interdependent Command Lines**

```bash
> const sayHello = "HI"
undefined
> console.log(sayHello)
HI
undefined
>
```

In the example in Listing 3.4, you assign a value to the `sayHello`
constant. This constant is used again in the output in the subsequent
statement. Among the most important features of the Node.js REPL
is the auto-completion function. If you press the (Tab) key without
entering anything else, you’ll get a list of all available objects. If you
use the auto-complete function in conjunction with one or more
letters, only the matching suggestions will be displayed. Another
feature worth mentioning is the multiline commands. As you can see
in Listing 3.3, the function code isn’t entered on a single line but on
several lines. An uncompleted command is indicated by three dots
instead of the greater-than sign as the command prompt. Multiline
commands can be achieved, for example, by unfinished code blocks
or a plus operator for calculation or string concatenation at the end of
the line.

### 3.1.2 Other REPL Commands
One of the special features of the Node.js REPL is that it provides
you with a few more commands to control the REPL in addition to
the JavaScript command set. The commands always start with a
period and don’t have to end with a semicolon. Table 3.1 contains an
overview of these commands.

![img](img/1.png)

There are two options available to exit the REPL: using the .exit
command or pressing (Ctrl)+(D), which will also terminate the
process immediately. Alternatively, you can press (Ctrl)+(C) twice.

The .break and .clear commands are used when the command line
is blocked by incorrect input. Listing 3.5 shows a use case for these
commands.


### 3.1.3 Saving and Loading in the REPL

### 3.1.4 Context of the REPL
### 3.1.5 REPL History


### 3.1.6 REPL Mode
### 3.1.7 Searching in the REPL
### 3.1.8 Asynchronous Operations in the REPL

## 3.2 The First Application

###
###
###
###