# :crocodile: Developing a Programming Language, CMPSC 201 Fall 2020: LAB 02 Assignment

## DUE: October 6th by 3:00pm

[![Actions Status](../../workflows/build/badge.svg)](../../actions)

## Table of Contents

- [Summary](#summary)

- [Objectives](#objectives)

- [Reading Assignment](#reading-assignment)

- [Accessing the Repository](#accessing-the-repository)

- [Tasks](#tasks)

  - [Scopes in JavaScript](#scopes-in-javascript)

  - [Frames](#frames)

  - [Stack Structure in Java](#stack-structure-in-java)

  - [A stack machine computation](#a-stack-machine-computation)

  - [Optimization](#optimization)

- [Running and Testing](#running-and-testing)

  - [Docker](#docker)

  - [GatorGrader](#gatorgrader)

  - [GitHub Actions CI](#github-actions-ci)

- [Evaluation](#evaluation)

- [Problems](problems)

## Summary

Designed for use with [GitHub Classroom](https://classroom.github.com/), this repository contains starter materials for lab 03 in [Computer Science 201 Fall 2020](https://cs.allegheny.edu/sites/jjumadinova/teaching/201). The lab03 assignment invites individuals to experiment with scoping.

Please watch a video introducing this lab assignment under the course's YouTube playlist: [Lab 03 Assignment Introduction](https://www.youtube.complaylist?list=PLz9YRLfRGO9JpJfVknMPnK_jagA0mgxN0)

## Objectives

- To understand the scope rules and issues. 
- To experiment, visualize and study the stack structure in JavaScript and in Java. 
- To analyze the code optimization. 

## Reading Assignment

To understand the concepts covered in this assignment, you should read Chapter 3 of the "Programming Language Pragmatics" textbook. You should also review questions and correct answers in activity5.

If you have not done so already, please read all of the relevant [GitHub Guides](https://guides.github.com/) that explain how to use many of the features that GitHub provides. In particular, please make sure that you have read guides such as "Understanding the GitHub flow", "Mastering Markdown" and "Documenting Your Projects on GitHub"; each of them will help you to understand how to use both GitHub and GitHub Classroom.

## Accessing the Repository

Please go into the #labs channel in our Slack team and find the announcement that provides a link for it. Copy this link and paste it into your web browser. Now, you should accept the laboratory assignment and see that a repository containing your GitHub username in its title was created for you. You can clone this repository and proceed with the tasks of the assignment.

## Tasks

For this laboratory assignment, you will complete a set of small experiments to gain a deeper understanding into scoping and code optimization related to scopes. The main deliverable of this assignment is the lab report document. 

### Scopes in JavaScript

Consider the following JavaScript program - what value is printed by the final line—is it "hello" or is it "10"?

```
        var x = "hello";

        function f() {
           x = 10;
           console.log("x ="+x);
           var x;
        }

        f();
        console.log("x="+x); /* What gets printed, "hello" or 10? */
```
    In your report, answer the question above (easy! just run it!), then
(a) explain how JavaScript's "function scope'' rule is interpreted,
and (b) state whether or not JavaScript requires "declare before use''
for variables.


### Frames

Go to the [PythonTutor Website](http://www.pythontutor.com) and click
on the link to "Start writing and visualizing code now!''

From the dropdown menu, choose JavaScript. Enter the following
code:  

```
     function f(x) {
       g(x+1);
     }
     function g(x) {
       console.log("in g, x ="+x);
     }
     f(3);
```

Click the "Visualize Execution'' button and then keep pressing the
"Next" button, watching the animation on the right side at each
step.

In your report document, provide a brief (one paragraph) explanation of the various stack frames that appear and disappear.

### Stack Structure in Java

Generate the JVM bytecode for the Java class `Stack1.java` (in the "src" directory). There is no "main" here, so you can’t run this, but you can still compile it and view the bytecode with either jbe or the javap -c command (refer to activity1).
In bytecode, the instructions "iload", "dload", "istore", and "dstore" take a numeric argument that specifies a location in the activation record (or frame). (Sometimes this argument is part of the instruction name, e.g, "iload_1"). In your report, "draw" the portion of the frame containing the parameters and local variables of function `f`, showing where each parameter `i`, `j`, `a`, etc., and each local variable sum, etc., appears in the frame. By "draw" I just mean something like this:

```
        1:   name of variable in frame location 1
        2:   name of variable in frame location 2
        3:   name of variable in frame locations 3 and 4 *
        5:     etc.
```
* Recall that a `double` takes twice as many spaces as an `int`.

### A stack machine computation

Generate the byte code for program `Stack2.java`. Assume that function `f` is called with `x = 10, y = 20`. "Draw" the frame for `f` (as in the previous section). Then "draw" the contents of the stack after each line of bytecode in function `f`. If the stack contains the value of a variable, name it. For instance, after the first two lines of bytecode are executed, the stack looks like this (I’m assuming the stack grows upward):
```
20 (y) 
10 (x)
```

and after the third line it looks like:
```
30
```

Remember how a stack machine works: operators like "add" pop their operands off the stack and then push the result (the above example shows how `x` and `y` are pushed on the stack, then they are popped and the value of `x+y` is pushed onto the stack.)

## Optimization

Look once more at Java program `Stack2.java` and its bytecode. How could this bytecode be optimized, i.e., shortened to fewer instructions? Answer this question, explaining and showing your optimized bytecode, in your document. (Feel free to experiment with the jbe editor.)


### Docker

To run your Python program using Docker Desktop, you need to first create a Docker image and then create and run the Docker container, using the following two commands, which are appropriate for your operating system.

_Mac/Linux:_

`docker build -t sly .`

`docker run --rm -v $(pwd)/src:/root sly python3 lab02.py`

_Windows:_

`docker build -t sly .`

`docker run --rm -v "%cd%/src":/root sly python3 lab02.py`

### GatorGrader

To assess the minimum completeness of the lab submission materials, you can use the GatorGrader tool. Once you have installed [Docker Desktop](https://www.docker.com/products/docker-desktop), you can use the following `docker run` command to start `gradle grade` as a containerized application, using the [DockaGator](https://github.com/GatorEducator/dockagator) Docker image available on [DockerHub](https://cloud.docker.com/u/gatoreducator/repository/docker/gatoreducator/dockagator).

```bash
docker run --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator
```

This command will use `"$(pwd)"` (i.e., the current directory) as the project directory and `"$HOME/.dockagator"` as the cached GatorGrader directory. Please note that both of these directories must exist, although only the project directory must contain something. Generally, the project directory should contain the source code and technical writing of this assignment, as provided to a student through GitHub. Additionally, the cache directory should not contain anything other than directories and programs created by DockaGator, thus ensuring that they are not otherwise overwritten during the completion of the assignment. To ensure that the previous command will work correctly, you should create the cache directory by running the command `mkdir $HOME/.dockagator`. If the above `docker run` command does not work correctly on the Windows operating system, you may need to instead run the following command to work around limitations in the terminal window:

```bash
docker run --rm --name dockagator \
  -v "$(pwd):/project" \
  -v "$HOME/.dockagator:/root/.local/share" \
  gatoreducator/dockagator
```

Since the above `docker run` command uses a Docker images that, by default, runs `gradle grade` and then exits the Docker container, you may want to instead run the following command so that you enter an "interactive terminal" that will allow you to repeatedly run commands within the Docker container.

```bash
docker run -it --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator /bin/bash
```

Once you have typed this command, you can use the [GatorGrader tool](https://github.com/GatorEducator/gatorgrader) in the Docker container by typing the command `gradle grade` in your terminal. Running this command will produce a lot of output that you should carefully inspect. If GatorGrader's output shows that there are no mistakes in the assignment, then your source code and writing are passing all of the automated baseline checks. However, if the output indicates that there are mistakes, then you will need to understand what they are and then try to fix them.

Here are some additional commands that you may need to run when using Docker:

- `docker info`: display information about how Docker runs on your workstation
- `docker images`: show the Docker images installed on your workstation
- `docker container list`: list the active images running on your workstation
- `docker system prune`: remove many types of "dangling" components from your workstation
- `docker image prune`: remove all "dangling" docker images from your workstation
- `docker container prune`: remove all stopped docker containers from your workstation
- `docker container stop ID`: stop the running container with specified ID
- `docker rmi $(docker images -q) --force`: remove all docker images from your workstation

### GitHub Actions CI

GitHub Actions CI is configured to check the Markdown files in the repository with "mdl". If your program and the writing meets the minimal established requirements, then you will see a green :heavy_check_mark: in the listing of commits in GitHub. If your submission does not meet the requirements, a red :heavy_multiplication_x: will appear instead. Since this assignment contains a large creative and open-ended portion, the majority of your lab grade will be based on the satisfaction of the requirements outlined in the previous sections.

## Evaluation

The grade that a student receives on this assignment will have the following components. In addition to these three main components, student's grade may be affected by their adherence or the lack of adherence to the [Code of Conduct](https://github.com/allegheny-computer-science-201-f2020/lab01-cs201f2020/blob/main/conduct.md) developed for this course.

Percentage of Correct GatorGrader Checks and GitHub Actions CI Build Status [up to 15%]: Students are encouraged to repeatedly revise their submission to ensure that it passes all of GatorGrader's checks and receives a CI pass.

Mastery of Technical Writing [up to 15%]: Students will also receive a portion of the lab grade when the responses to the technical writing questions presented in the 'writing/report.md' reveal a mastery of both writing skills and conceptual and technical knowledge. To receive this portion of the grade, the submitted writing should have correct spelling, grammar, and punctuation in addition to following the rules of Markdown and providing conceptually and technically accurate answers.

Mastery of Technical Knowledge and Skills [up to 70%]: Students will receive a largest portion of their assignment grade when their project implementation reveals that they have mastered all of the technical knowledge and skills developed during the completion of this project. As a part of this grade, the instructor will assess aspects of the project including, but not limited to, the designed grammar, correctness of the scanner and the parser, the completeness and correctness of the test cases, and the use of effective source code comments, and Git commit messages.

## Problems

If you have any problems with this assignment, then please create an issue in this repository using the "Issues" link at the top of this site.
