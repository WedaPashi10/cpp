# Smart pointers

It is introduced in `C++11` version, specifically deals with ways to avoid memory leaks.

A Smart Pointer is a wrapper class over a pointer with an operator like `*` and `->` overloaded. The objects of the smart pointer class look like normal pointers. But, unlike normal pointers it deallocates and frees the destroyed object memory. So, we don’t need to delete it as Smart Pointer does will handle it.

The idea is to design a class with a pointer, destructor and overloaded operators like `*` and `->`. Since the destructor is automatically called when an object goes out of scope, we can add code to `delete` the borrowed memory so that there won't be any memory leakage.

One can assume that we must create a smart pointer for every object if it deals with dynamic memory, which is chaotic. So thankfully using Templates we can simplify things.

    // A generic smart pointer class
    template <class T>
    class SmartPtr {
        T* ptr; // Actual pointer
    public:
        // Constructor
        explicit SmartPtr(T* p = NULL) { ptr = p; }
        // Destructor
        ~SmartPtr() { delete (ptr); }
        // Overloading dereferencing operator
        T& operator*() { return *ptr; }
        // Overloading arrow operator so that members of T can be accessed like a pointer
        T* operator->() { return ptr; }
    };
    
Apart from the implementation above, there are ways to levarage smart pointers, that are introduced in `C++11` and onwards.
This feature was introduced in `<memory>` header, providing a convenient way managing the dynamically allocated memory.

### Types of smart pointers:

- _unique_ptr:_ As the name suggests, at a time only one pointer can point to the object.   
- _shared_ptr:_ As the name suggests, at a time multiple pointers can point to a common object. It maintains a reference counter which indicates the number of pointers pointing to the common object.
- _weak_ptr:_ At a time multiple pointers can point to a common object, its just that, it doesn't maintain a reference counter as _shared_ptr_ does!

