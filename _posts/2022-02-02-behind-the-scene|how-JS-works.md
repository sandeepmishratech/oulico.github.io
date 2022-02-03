---
layout: post
title: "Behind the scene: How JavaScipt Works 1"
date: 2022-02-02 11:09:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript behind_the_scenes  
---



## Definition of JavaScript

Javascript is...

- **High-level**
- **Object-oriented**
- **Multi-Paradigm**
- **Interpreted or Just-In-Time compiled**
- **Dynamic**
- **Single-threaded**
- **Garbage-collected** Programming language
- With **first-class functions** and a non-blocking **event loop concurrency model**







## Engine

A JS engine is a program executes JavaScript Code.

Every browser has its own JavaScript Engine.



The most well known engine is Google's V8.

The V8 engine powers Google Chrome, and Node.js.



Understanding what the engine is but the most important thing to understand is **its components and how it works**.



## Components of a JS engine

JS engine containes a `call stack` and a `heap`.

- Call stack : where your code is actually excited using `exception contexts`.
- Heap : an unstructured memory pool which stores all the objects that your application needs.



## How the code is compiled to machine code

### 1.

First of all you need to know about the difference between `compilation` and `interpretation`.

### - Compilation

> Entire code is converted into machine code at once, and written to a binary file that can be executed by a computer

>And this machine code is then written into a portable file that can be executed on any computer.

![image-20220202111106975](/assets/img/2022-02-02-behind-the-scene%7Chow-JS-works/image-20220202111106975.png)

### - Interpretation

> There is an interpreter which runs through the source code and executes it line by line.

> The source code still need to be converted into machine code, but it simply happens right before it's executed and not a head of time.

![image-20220202111722397](/assets/img/2022-02-02-behind-the-scene%7Chow-JS-works/image-20220202111722397.png)

JS used to be a purely interpreted language but the problem with interpreted languages is that they are much, much slower than compiled languages.

Many people still think that JS is an interpreted language but that's not true anymore.

Modern JavaScript engine now use a mix between compilation and interpretation which is called **just-in-time** compliation.

### - JIT(Just-In-Time)

> Entire code is converted into machine code at once, then executed immediately.

> So we have the two steps of regular agead of time compilation but there is no portable file to execute, and the execution happens immediately after a compilation.

![image-20220202112500387](/assets/img/2022-02-02-behind-the-scene%7Chow-JS-works/image-20220202112500387.png)



### 2. How this works

![image-20220202113517307](/assets/img/2022-02-02-behind-the-scene%7Chow-JS-works/image-20220202113517307.png)

1. Parsing (reading the code)
   - during the process, the code is parsed into a data structure called **the abstract syntax tree (AST)**. This works by splitting up each line of code into pieces that are meaningful to the language like the `const` or `function keywords`, and thenn saving all these pieces into the tree in a structured way. This step also checks if there are any syntax errors and the resulting tree will later be used to generate the machine code.
2. Compilation 
   -  it takes the generated AST and compiles it into machine code
3. Execution
   - This machine code then gets executed right away in `Call Stack`





JavaScript engines create a very unoptimized version of machine code in the beginning so that it can start executing as fast as possible.

Then in the background, this code is being optimized and recompiled during the already running program execution.

This can be done most of times and after each optimization, the unoptimized code is simply swept for the new more optimized code without ever stopping execution of course.

and this process is what makes modern engines such as the V-Eight so fast and all this parsing, compilation and optimization happens in some special threads inside the engine that we cannot access from your code.

So completely separate from the main thread that is basically running into call stack executing our own code.

Now different engines implements in slightly differnet ways, but in a nutshell this is what modern Just-in_time compilation looks like for JavaScript.



## JavaScript Runtime



We can imagine a `JS runtime` as a big box or a big container which includes all the things that we need in order to use JavaScript. 

In the runtime there's always a JS engine.

But in order to work properly, we also need access to the web `API`s, everything related to the `DOM` or `timer`s or even the `console.log` that we use all the time.

So essentially web APIs are functionalities provided to the engine, but which are actually not part of the JavaScript language itself.JS gets access to these APIs through the global window objet.

But still the web APIs are also part of the runtime, because a runtime is just like a box that contains all the JavaScript related stuff that we need.

Next, a typical JavaScript runtime also includes a `callback queue`. This is a data sturcture that contains all the callback functions that are ready to be executed.

For example, we attach event hanldler functions to DOM elements like a button to react to certain events.

And these `event handler functions` are also called `callback functions`.

So as the event happens, for example a click, the callback function will be called. And here is how that actually works behind the scenes.

## How a callback function works

So the first thing that actually happens after the event is that the callback function is put into the callback queue.

When the stack is empty, the callbacke function is passed to the stack so that it cam be excuted.

And this happens by something called the event loop.

So basically the `event loop` takes `callback functions` from the `callback queue` and puts them in the `call stack` so that they can be executed.

