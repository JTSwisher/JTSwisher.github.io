---
layout: post
title:      "Hoisting in JavaScript"
date:       2020-08-31 18:04:53 +0000
permalink:  hoisting_in_javascript
---

[Medium Article](https://medium.com/@jefftswisher/hoisting-in-javascript-8efa9a391598) 

In JavaScript, there can be a lot of concepts that are hard to grasp for new Developers. Hoisting being one of them, in an attempt to help myself understand it better and hopefully, you as well lets dive into this concept further.

Hoisting will occur at both the variable and function level. A general definition would state that the declarations of variables and functions are moved(hoisted) to the top of the code within their respective scope. If the declaration occurs within the global scope it is moved to the top of that scope and the same can be said for local scope declarations. Hoisting will only move the declarations, it does not execute assignment statements. Although it may sound like your code is being physically moved within your codebase, that is not the case. These declarations are simply being stored in memory during the creation phase of the execution context.

    Variables are initially set to a value of undefined at the time of hoisting.

Image for post
Image for post

    As we can see above we have “console.log(a)” on both lines 2 and 4. But we are getting two different results from both “console.log” functions. What is happening here exactly? I think it would be safe to assume that we would expect to receive “ReferenceError: a is not defined” from our first “console.log” as “a” did not exist before we referenced it.
    But take a look below at a representation of what are code would need to look like to achieve the same results as above if hoisting did not occur.

Image for post
Image for post

It is important to understand in regards to the above example that when hoisting occurred for “var a;” it did not physically move to the top of our function as shown. That first “console.log(a)” is referencing the original declaration of “a” from the first example that was stored in memory and initialized with a value of “undefined”.

    Take a look at the example below! Weird huh? Where is our undefined value that was associated with “var a;” in the example above? While it is true that all declarations (var, let, const, and class) are hoisted, let and const declarations remain uninitialized. They will only get initialized during the execution phase of the execution context. This means we cannot access the variable before the point in which it was declared and is evaluated during runtime.

Image for post
Image for post

So far we have touched mainly on variable hoisting and haven't talked much about function hoisting. We can classify functions as either “function declarations” or “function expressions,” declarations will be hoisted while expressions will not.

    Consider the following example. We would expect that we would have to declare and call our function in this manner for it to work.

Image for post
Image for post

    However, thanks to function hoisting we are allowed to call our functions before they have been declared.

Image for post
Image for post

While we could dive deeper into hoisting the information above should give you a basic understanding of hoisting and put you in a position to either benefit from what’s happening under the hood or avoid some pesky bugs down the road! If you have anything to add leave a comment below, happy coding!

