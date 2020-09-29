# LAB 03 Report

## Add your name

### 1\. Scopes in JavaScript

Study the JavaScript program named `Scope.js` inside "src" directory. Run the program to see the value that is printed by the final line- is it "hello" or is it "10"? You can run the program by entering the `localhost` window using the course Docker image (see README for instructions), navigating inside "environment/src" directories in the terminal, and typing `node Scope.js`. Provide answers to the following questions.

_Questions_: 1.1\. Output:

```
TODO
```

1.2\. In the `Scope.js` program, write a second function called "hola" that creates another `greeting` variable using `var` keyword in JavaScript, initializes it to the value of "Hola", and prints the value of `greeting`. Then, add a call to this new function called "hola" at the end of function `privet`. Include the output below:

```
TODO
```

1.3\. Based on the `Scope.js` program and your understanding of scoping, explain how JavaScript's "function scope'' rule is interpreted. TODO

1.4\. State whether or not JavaScript requires "declare before use'' for variables. 

TODO

### 2\. Frames

Go to the [PythonTutor Website](http://www.pythontutor.com) and click on the link to "Start writing and visualizing code now!''

From the dropdown menu, choose JavaScript. Enter the following code:

```
     function f(x) {
       g(x+1);
     }
     function g(x) {
       console.log("in g, x = " + x);
     }
     f(3);
```

Click the "Visualize Execution'' button and then keep pressing the "Next" button, watching the animation on the right side at each step.

_Question_: 2\. Provide a brief (one paragraph) explanation of the various stack frames that appear and disappear. 

TODO

### 3\. Stack Structure in Java

Java bytecode is the virtual instruction set of the Java virtual machine. It features one-byte instruction with 256 possible opcodes and uses stack-based computation. Java bytecode instructions operates on 9 main different types: the 8 primitives types: `byte` , `char`, `short`, `int`, `long`, `float`, `double` (`boolean`, `byte`, `short` and `char` are sometimes treated as `int`) and reference (a reference is a pointer to an Object in the heap). `long` and `double` values takes two slots in the operand stack and local variables (all the other types takes one). Each mnemonic (textual form of an operation) is encoded as a byte in the class file, which is called an operation code or opcode. Some examples of mnemonics include:

- `iadd`: add two integers
- `fmul`: multiply two floats
- `lload1`: load a long value from the local variable 1

Instructions dealing with the stack or local variables start with a letter corresponding to the type. For example, `iadd` adds two integers, whereas `dadd` adda two doubles. Arguments follow an instruction, for example, `bipush 5` loads a byte onto the stack and `iconst0` loads 0 onto the stack.

To learn more about Java bytecode specification and instructions consider the following resources:

- [The Java Virtual Machine Specification](http://docs.oracle.com/javase/specs/jvms/se8/html/index.html)
- [Instructions listing](https://en.wikipedia.org/wiki/Java_bytecode_instruction_listings)
- [JVM Instruction Set Documentation](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-6.html).

Generate the JVM bytecode for the Java class `Stack1.java` (in the "src" directory). There is no "main" here, so you can't run this, but you can still compile it using `javac Stack1.java` command in the terminal of the "src" directory (where this program is located) and view the bytecode with `javap -c Stack1.class` command. In bytecode, the instructions "iload", "dload", "istore", and "dstore" take a numeric argument that specifies a location in the activation record (or frame). Sometimes this argument is part of the instruction name, e.g, "iload_1".

_Question_: 3\. Specify. the portion of the frame containing the parameters and local variables of function `func`, showing where each parameter `num1`, `num2`, `numd1`, etc., and each local variable sum, etc., appears in the frame. For example, the details you are required to provide are as follows:

```
        1:   name of variable in frame location 1
        2:   name of variable in frame location 2
        3:   name of variable in frame locations 3 and 4 ^
        5:     etc.
```

^ Recall that a `double` takes twice as many spaces as an `int`.

TODO

### 4\. A stack machine computation

Generate the byte code for program `Stack2.java`. Assume that function `func` is called with `num1 = 10, num2 = 20`. If the stack contains the value of a variable, name it. For instance, after the first two lines of bytecode are executed, the stack looks like this (I'm assuming the stack grows upward):

```
20 (num2)
10 (num1)
```

and after the third line it looks like:

```
30
```

Remember how a stack machine works: operators like "add" pop their operands from the stack and then push the result (the above example shows how `num1` and `num2` are pushed on the stack, then they are popped and the value of `num1 + num2` is pushed onto the stack.)

_Question_: 4\. "Draw" the frame for `func` (as in the previous question 3). Then "draw" the contents of the stack after each line of bytecode in function `func`. 

TODO

### Reflection

What were your biggest learning points during this lab and what challenges have you  encountered during this lab?

TODO
