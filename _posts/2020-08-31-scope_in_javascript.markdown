---
layout: post
title:      "Scope in JavaScript"
date:       2020-08-31 18:04:10 +0000
permalink:  scope_in_javascript
---


[Medium Article](https://medium.com/@jefftswisher/scope-in-javascript-48e08329f090) 

The concept of Scope in regards to JavaScript can be a bit hard to wrap your head around as a new Developer. Lets dive into this concept further for a more in-depth look.
Scope

In JavaScript, there are two types of “scoping” that you will encounter. There is Global scope and Local scope. These scopes in relation to a variable will be determined by the location of the variable declaration.

Global Scope

Global scope applies to any variable that is declared outside of a function in the top-level scope. Variables that have a global scope can be accessed anywhere in your code.

    “b” is accessible from within the functions local scope due to “b” being scoped globally.

Image for post
Image for post

    Also important to note, variables declared without (var, const or let) are scoped globally.

Image for post
Image for post

Local Scope

Each function you create with JavaScript has its own local scope, as such when you declare a variable from within a function it is scoped locally to that function. This means the locally scoped variable is unavailable outside of that function, however, it will be available to any nested functions within the parent function through the scope chain.

    “b” is not accessible outside of its local scope.

Image for post
Image for post

    “b” is available to the “nestedFunc” function through the scope chain or whats called “lexical scoping.” The nested function has access to all variables that are declared in its parent functions local scope and so on up the scope chain all the way to the global scope.

Image for post
Image for post

    In this example, we have two separate declarations of the variable “b”, while in the previous example we logged the value from the parent scope. The nested function will always check for a local instance of the variable we are referencing, if it does not find what it is looking for in its current scope it will move up the scope chain until it does or throws an error.

Image for post
Image for post

    “b” is locally scoped to the “nestedScope” function here. We cannot access it from the parent “scope” function, the scope chain does not work from the top down.

Image for post
Image for post

Thus far we have looked at local scope from a function scope standpoint. With ECMA script 6 (ES6) the concept of block scope was introduced together with the new variable declaration keywords const and let.

Block Scope

Block scope is defined within for/while loops and if/switch statements. const and let are the only variable declaration keywords that support local scope as noted in the code below.
Image for post
Image for post

Whew, that was a lot of scope talk, I hope this helps you understand this concept a bit better. If I missed anything or you have anything to add leave a comment below. Happy Coding!
