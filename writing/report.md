# LAB 03 Report

## Names

### 1. Scopes in JavaScript

Consider the following JavaScript program - what value is printed by the final line—is it "hello" or is it "10"?

```
var greeting = "hello";

function privet() {
   greeting = 10;
   console.log("greeting = " + x);
   var greeting;
}

privet();
console.log("greeting = " + x);

```

*Questions*:
1.1. Output:
```
TODO
```
1.2. Explain how JavaScript's "function scope'' rule is interpreted.
TODO

1.3. State whether or not JavaScript requires "declare before use''
for variables.
TODO

### 2. Frames

Go to the [PythonTutor Website](http://www.pythontutor.com) and click
on the link to "Start writing and visualizing code now!''

From the dropdown menu, choose JavaScript. Enter the following
code:  

```
     function f(x) {
       g(x+1);
     }
     function g(x) {
       console.log("in g, x = " + x);
     }
     f(3);
```

Click the "Visualize Execution'' button and then keep pressing the
"Next" button, watching the animation on the right side at each
step.

*Question*:
2. Provide a brief (one paragraph) explanation of the various stack frames that appear and disappear.
TODO

### 3. Stack Structure in Java

Generate the JVM bytecode for the Java class `Stack1.java` (in the "src" directory). There is no "main" here, so you can’t run this, but you can still compile it and view the bytecode with either jbe or the javap -c command (refer to activity1).
In bytecode, the instructions "iload", "dload", "istore", and "dstore" take a numeric argument that specifies a location in the activation record (or frame). (Sometimes this argument is part of the instruction name, e.g, "iload_1"). 

*Question*:
3. "Draw" the portion of the frame containing the parameters and local variables of function `f`, showing where each parameter `i`, `j`, `a`, etc., and each local variable sum, etc., appears in the frame. By "draw" I just mean something like this:

```
        1:   name of variable in frame location 1
        2:   name of variable in frame location 2
        3:   name of variable in frame locations 3 and 4 *
        5:     etc.
```
* Recall that a `double` takes twice as many spaces as an `int`.

TODO

### 4. A stack machine computation

Generate the byte code for program `Stack2.java`. Assume that function `f` is called with `x = 10, y = 20`. If the stack contains the value of a variable, name it. For instance, after the first two lines of bytecode are executed, the stack looks like this (I’m assuming the stack grows upward):
```
20 (y) 
10 (x)
```

and after the third line it looks like:
```
30
```

Remember how a stack machine works: operators like "add" pop their operands off the stack and then push the result (the above example shows how `x` and `y` are pushed on the stack, then they are popped and the value of `x+y` is pushed onto the stack.)

*Question*:
4. "Draw" the frame for `f` (as in the previous section). Then "draw" the contents of the stack after each line of bytecode in function `f`. 
TODO

### Reflection
