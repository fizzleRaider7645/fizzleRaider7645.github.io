---
layout: post
title:      "Callbacks and Arrow Functions"
date:       2019-09-10 13:29:32 +0000
permalink:  callbacks_and_arrow_functions
---


ECMAScript introduced a new way of making functions in ES6, known as Arrow Functions. Arrow functions offer shorter syntax and address several issues that previously had to be considered when creating functions. Foremost among those considerations is how ‘this’ is handled.

When a standard function is invoked within another function, the context of ‘this’ is assigned to the default `window` context. This can become problematic if the callback needs to have access to the `this` of the of the function it’s being called in, in order to function properly. The ‘bind()’ method was often used to remedy this issue. The ‘bind()’ method creates a new function that has it’s ‘this’ keyword set to a provided value. In the case of callbacks, it would be the ‘this’ value of the function the callback is being called from.

However, Arrow Functions do not have their own ’this’, but rather, they use whatever context they are declared in. Now, a callback no longer necessarily needs to be bound via the ‘bind()’, but already has access to the this of the higher function. This allows for cleaner code, which is further bolstered by Arrow Functions shorter syntactical form. You can find the various implementations in the [MDN web docs](http://https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions). 

There are many potential benefits to using Arrow Functions, though deciding on whether an Arrow Function is preferred over a Standard Function is highly dependent on the use case. Understanding the uses/pros and cons of each is essential is making that decision. In the case of callback functions, utilizing Arrow Functions makes code much clearer, and for the most part, can eliminate the need to use `.bind()`.

