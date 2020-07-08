# Lesson 2 - Intro to C

## Preface

For these lessons, we'll be using C as our programming language of choice. If
the goal of these lessons was to teach you generally how to program, we'd
probably start with a higher level language with many convenience features such
as Python or JavaScript.

C has the double-edged property of doing very little for you besides what you
ask it to. When trying to build a responsive webapp, or enterprise-scale
application, this works against the language. But when trying to get hardware to
do exactly what you want it to do and exploring the underpinning of what makes
programs go, the explicitness of the language brings clarity.

## The World's Fastest Intro to C

Since these lessons assume that you know how to program already, here's a
rundown on C's basic syntax (more advanced things we will be going into in later
lessons).

### Primitive Data Types

| Data Type | Size         | Description                          |
|-----------|--------------|--------------------------------------|
| char      | 1 byte       | A single ASCII character             |
| int       | 2 or 4 bytes | An integer. Size depends on compiler |
| float     | 4 bytes      | Floating point number                |
| void      | 1 byte       | Ignore for now :)                    |

### Basic Flow Control

```c
// Variable creation
int age = 5;

// if/else if/else
if (age > 4)
{
    return true;
}
else if (age == 1)
{
    return true;
} else {
    // Variables are mutable by default
    age = 27;
}

// switch statement
switch (age)
{
case 2:
    return false;
    break;
case 5:
    // No "break;" means this falls through to the next statement
default:
    return true;
}
```

### Loops

```c
// while loop
while (age > 10)
{
    // Can modify/reassign with one operator
    age -= 5;
}

// do while. Like a while, but executes loop body at least once
do
{
    age += 2;
} while (age % 2 == 1);

// for loop. Like a while loop with book keeping.
//
// The expressions in the parentheses are, in order:
//   initialization
//   expression that, if true, lets the loop repeat again
//   update
// Each expression is optional
for (int i = 1; i <= 10; i *= 2)
{
    // This inner boddy will run 4 times. The first time i will be 1, the second
    // time i will be 2, then 4, then 8. The following time, i will be 16, which
    // is greater than 10, which will break out of the loop.
}
```

### Functions

```c
// Functions have a return type and can take typed parameters.
int MyFunction(bool parameterOne)
{
    if (parameterOne) {
        return 7;
    }
    return 5;
}

// Main always has this signature. It returns an integer as a status, argc holds
// the number of arguments passed to the program on the command line, and argv
// holds the contents of those arguments. We will dive more into the *'s later.
int main(int argc, char** argv)
{
    // Calls our function we defined above. It's important to note that the
    // compiler needs to see the function definition before the function can be
    // called. That is to say, if we defined MyFunction in the same file as
    // main, but after the main function, this would be an error.
    MyFunction(true);
    return 0; // Returning 0 means everything went well.
}
```

### Libraries and Imports

C's concept of importing code from other files is incredibly naive. You can include other header files (files with definitions you care about) as follows:

```c
// Includes a file from a predetermined file path based on your system.
// This line includes the IO functions from the C standard library.
#include <stdio.h>

// Includes a file from a path relative to the current file.
#include "helper.c"
```

These lines that start with `#` are called preprocessor directives. They tell
the preprocessing program to do _something_ with the text here before it sends
it over to the actual code compiler for compilation. In the case of the
`#include` directive, we're saying "copy the contents of the file I mention, and
paste its contents RIGHT HERE."

There are a lot of advanced concepts to go over here, but for the purposes of
our lessons, we're primarily going to be including `stdio.h` and nothing
further. If you're interested in following up on your own, Google
`c header files`.

### Compilation

As we discussed in lesson 1, you can compile your code by invoking `clang` with
a list of files you wish to compile together:

```shell
$ clang main.c helper.c otherlib.c
```

This will create an executable in the directory you ran the command from called
`a.out`. Invoking `a.out` will run the code:

```shell
$ ./a.out
Hello, world!
```

You can change the name of the executable by passing a name via the `-o` flag:

```shell
$ ls
main.c
$ clang -o my_prog main.c
$ ls
main.c my_prog
$ ./myprog
Hello, world!
```

This _can_ get complicated, and as such there are tools (such as `make`) to
automate parts of it. Since we're only going to be dealing with small programs
of one or two files, manually invoking `clang` shouldn't get too difficult.

## Conclusion

This was a very brief, very reductive intro to the syntax of C. In fact we
glossed over many of the more powerful features C provides (to be looked into in
a future lesson of course). This lesson doesn't have a specific task to
complete, but you should play around with the information above until you can do
the following:

*   Compile and execute your code
*   Add functions and call them from `main`
*   Print information from your code of different data types via `printf`