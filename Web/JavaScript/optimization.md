[Mathias Bynens - V8 internals for JavaScript developers](https://www.youtube.com/watch?v=m9cTaYI95Zc)
1. do not mix types in array. Smi -> Double -> Regular. prevent elements kind transitions.
2. do not create hole in array. prefer packed array
3. avoid array like objects, use real array instead.
4. avoid out-of-bounds reads.
5. array = []; array.push(x); continuesly push elements to array will slow down array creation. because the v8 needs to continuesly allocate new spaces if out of bounds.