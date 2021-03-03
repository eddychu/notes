## Standard Library

Set and Map WeakMap WeakSet

important difference is WeakMap and WeakSet don't prevent their key values from being garbage collected.

regular Set and Map holds strong references to its key values.

WeakMap WeakSet keeps weak references to its key values so that they are not reachable through WeakMap, and their presence in the map does not prevent their memory from being reclaimed.

WeakMap keys must be objects or arrays; primitive values are not subject to
garbage collection and cannot be used as keys.

WeakMap is not iterable. cannot use keys(), values(), or forEach().


The intended use of WeakMap is to allow you to associate values with objects without
causing memory leaks. Suppose, for example, that you are writing a function that
takes an object argument and needs to perform some time-consuming computation
on that object. For efficiency, you’d like to cache the computed value for later reuse. If
you use a Map object to implement the cache, you will prevent any of the objects
from ever being reclaimed, but by using a WeakMap, you avoid this problem. (You
can often achieve a similar result using a private Symbol property to cache the com‐
puted value directly on the object.

WeakSet does not allow primitive values as members.
WeakSet is not iterable.




Array TypedArrays 
Regular expression and RegExp class
Date
Error
JSON object
Intl object
Console object
URL class
setTimeout() related functions




## Asynchronous

Promises, new in ES6, are objects that represent the not-yetavailable result of an asynchronous operation. The keywords async and await were
introduced in ES2017 and provide new syntax that simplifies asynchronous program‐
ming by allowing you to structure your Promise-based code as if it was synchronous.
Finally, asynchronous iterators and the for/await loop were introduced in ES2018
and allow you to work with streams of asynchronous events using simple loops that
appear synchronous.


### Promise

Promise.all
Promise.any
Promise.allSettled
Promise.race