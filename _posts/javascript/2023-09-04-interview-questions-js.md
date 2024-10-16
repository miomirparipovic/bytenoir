---
title: Interview questions JS
published: false
---

### Index

1. [What is JS?](#what-is-js)
2. [What is ECMAScript?](#what-is-ecmascript)
3. [What is JS engine?](#what-is-js-engine)
4. [What is a call stack?](#what-is-a-call-stack)
5. [What is a stack trace?](#what-is-a-stack-trace)
6. [What is a lexical environment?](#what-is-a-lexical-environment)
7. [What is an execution context?](#what-is-an-execution-context)
8. [What is a global execution context?](#what-is-a-global-execution-context)

### What is JS?

JS is a programming language that is one of the core technologies of the WWW, alongside HTML and CSS. It is a high-level, JIT compiled language that conforms to the ECMAScript standard.

JS has dynamic typing, prototype-based object-orientation, and first-class functions. It is multi-paradigm, supporting event-driven, functional, and imperative programming styles. It has many APIs available for working with text, dates, regular expressions, standard data structures, and the Document Object Model (DOM).

The ECMAScript standard does not include any input/output (I/O), such as networking, storage, or graphics facilities. In practice, the web browser or other runtime system provides JS APIs for I/O.

JS is a single-threaded language, which means it can run one line at a time, sequentially. JS can also be non-blocking and behave as if it were multi-threaded thanks to the help of asynchronous operations and browser's multi-threading capabilities, event loop, Web APIs, web workers, etc.

### What is ECMAScript?

ECMAScript, often abbreviated as ES, is a standard for a scripting language or a scripting language specification. JS is one of the well-known implementations of this standard.

ES defines the syntax and semantics, and provides guidelines for how these scripting languages should function.

ES is maintained by the ECMA International standards organization (**European Computer Manufacturer's Association**), specifically under the _Ecma Technical Committee 39_ (TC39).

So, in summary, the purpose of ES is:

- Defines language features.
- Ensures compatibility across different browsers and runtime environments.
- Standardizes APIs (defines standard APIs for common tasks, such as manipulating the DOM), etc.

### What is JS engine?

A JS engine is a _software component_ that executes JS code. Today, JS can execute not only in the browser, but also on the server, or any device that has a special program called the JS engine.

The first JS engines were mere interpreters, but all relevant modern engines use JIT (just-in-time) compilation for improved performance.

- The engine (embedded if it's a browser) reads ("parses") the script.
- Then it converts ("compiles") the script to machine code.
- And then the machine code runs, pretty fast.

The engine applies optimizations at each step of the process. It even watches the compiled script as it runs, analyzes the data that flows through it, and further optimizes the machine code based on that knowledge.

### What is a call stack?

A call stack (execution stack) is a stack data structure.

A call stack is a mechanism, or a concept, for JS to keep track of its place in a script that calls multiple functions - what function is currently being run and what functions are called from within that function, etc.

- When a script calls a function, the interpreter adds it's execution context to the call stack and runs the function.
- Any functions that are called by that function will cause creation of another execution context that is added to the call stack further up, and function will be run when its call is reached.
- When the current function is finished, the interpreter takes its execution context off the stack and resumes execution of the previous function (from its execution context) where it left off.
- If the stack takes up more space than it was assigned, a "stack overflow" error is thrown.

It's important to note that JS is a single-threaded language, which means it processes one task at a time. The concept of the call stack is crucial here. It's a data structure that _tracks the active execution contexts_. When a function is called, a new execution context is created and pushed onto the call stack. When a function finishes executing, its context is popped off the stack, and control returns to the previous context.

Furthermore, in modern JS environments (like browsers or Node.js), there are also asynchronous operations that introduce additional execution contexts, such as those for handling callbacks, promises, and async/await code. These asynchronous contexts interact with the main call stack through a mechanism called the _event loop_.

Execution stack works on a LIFO data structure way. It waits for the topmost execution context to return before executing the context below.

### What is a stack trace?

A stack trace is a _report of a list of the functions_, in order, that lead to a given point in a software program, usually an error or exception.

A stack trace is essentially a breadcrumb trail for your software.

In JS, when an error (such as an exception) occurs during the execution of your code, the runtime environment captures the current state of the call stack and generates a stack trace. This stack trace can be incredibly helpful for debugging, as it allows you to pinpoint the exact location where the error occurred.

You can easily see the stack trace in JS by adding the following into your code:

```js
console.trace();
```

### What is a lexical environment?

_Lexical environment_ is the internal JS's engine construct that consists of two parts:

- identifier-variable mapping
- reference to the outer (parent) lexical environment

'Identifier' refers to the name of variables and functions. 'Variable' is the reference to the actual object, including function type object or primitive value.

_Important_ "Lexical Environment" is a specification object: it only exists "theoretically" in the language specification to describe how things work. We can't get this object in our code and manipulate it directly.

So, lexical environment is a construct that describes where a portion of the code is located and what is surrounding it.

### What is an execution context?

There are lots of lexical environments, but which one is currently actually running is managed via what's called _execution contexts_.

Whenever code is run in JS, it's run inside an _execution context_.

_Execution context_ is the internal JS construct (an abstract object) to track execution of a function or the global code.

The JS engine maintains a stack data structure - _execution context stack_ or _call stack_, which contains these contexts. The global execution context stays at the bottom of this stack. A new execution context is created and pushed to the stack when execution of a function begins.

Anytime you execute or invoke a function, even if it's invoking itself, in JS a new execution context is created and placed on the execution stack. This execution context will have its own space for variables and functions, and 'this' variable for that function, it will go through that create phase and then it will execute the code within the function. If there is another function invocation, it's going to stop at that line of code and create another execution context and go through the same steps.

What is running in JS is the current code within the current execution context, which is the one at the top of the stack.

_Execution context_ is a wrapper to help manage the code that is running.

There are three main types of execution contexts:

- global,
- function, and
- eval (typically avoided due to security concerns).

### What is a global execution context?

The _global execution context_ is a concept in JS that represents the initial environment in which code starts running. It is created when a script is first loaded into the JS engine for execution. It sets up the foundation for all subsequent code execution within the script.

- It is created automatically on the load.
- It is the base execution context.
- It is the outermost context that encapsulates the entire script.
- Scope chain. The global execution context doesn't have an outer scope-it is the outermost context. It will establish a scope chain, which includes the global scope itself. This _link to the outer environment_ is 'null' at the level of the global execution context.
- 'this' keyword is set (a special variable 'this'). 'this' often refers to the global 'window' object (different in Nodejs).
- Once set up, the JS engine continues to execute the code within the global context execution.

_Global_ means that is accessible everywhere in your code. When we say global in JS, that means _not inside a function_. That means code or variables that aren't inside a function are global.

Even when your code file (script) is empty, a global execution context will be created with a _global object_ and _'this'_ keyword.

'window' and 'this' are the same object, in this context.

There is always _a global object_ when you're running JS.
