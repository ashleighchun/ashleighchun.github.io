---
layout: post
title:      "The Importance of Closures"
date:       2019-08-20 14:18:46 -0400
permalink:  the_importance_of_closures
---

Closure: the combination of a function bundled together (enclosed) with references to its surrounding state aka gives you access to an outer function’s scope from an inner function.
              They are created every time a function is created, at function creation time.
              To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function. 
              The inner function will have access to the variables in the outer function scope, even after the outer function has returned.
