# This pointer

To understand `this` pointer, it is important to know how objects look at functions and data members of a class.

1. Each object gets its own copy of the data member.  
2. All-access the same function definition as present in the code segment.  

Meaning, each object gets its own copy of data members and all objects share a single copy of member functions.
The compiler supplies an implicit pointer along with the names of the functions as ‘this’.
The ‘this’ pointer is passed as a hidden argument to all nonstatic member function calls and is available as a local variable within the body of all nonstatic functions. ‘this’ pointer is not available in static member functions as static member functions can be called without any object (with class name).
