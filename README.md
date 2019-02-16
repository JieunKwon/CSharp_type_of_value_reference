# CSharp_type_of_value_reference
Theory of Value vs Reference Types


# Value and Reference Types
There is another difference between structs and classes, and this is also the most important to understand.  Structs are value types, while classes are reference types, and the runtime deals with the two in different ways.  When a value-type instance is created, a single space in memory is allocated to store the value.  Primitive types such as int, float, bool and char are also value types, and work in the same way.  When the runtime deals with a value type, it's dealing directly with its underlying data and this can be very efficient, particularly with primitive types.

With reference types, however, an object is created in memory, and then handled through a separate reference—rather like a pointer.  Suppose Point is a struct, and Form is a class.  We can instantiate each as follows:

    Point p1 = new Point();         // Point is a *struct*
    Form f1 = new Form();           // Form is a *class*

In the first case, one space in memory is allocated for p1, wheras in the second case, two spaces are allocated: one for a Form object and another for its reference (f1).   

# Memory Allocation
The Common Language Runtime allocates memory for objects in two places: the stack and the heap.  The stack is a simple first-in last-out memory structure, and is highly efficient.  When a method is invoked, the CLR bookmarks the top of the stack.  The method then pushes data onto the stack as it executes.  When the method completes, the CLR just resets the stack to its previous bookmark—“popping” all the method’s memory allocations is one simple operation!

In contrast, the heap can be pictured as a random jumble of objects.  Its advantage is that it allows objects to be allocated or deallocated in a random order.  As we’ll see later, the heap requires the overhead of a memory manager and garbage collector to keep things in order.

# Stack and Heap in Memory

The stack is always used to store the following two things:

The reference portion of reference-typed local variables and parameters (such as the myTextBox reference)
Value-typed local variables and method parameters (structs, as well as integers, bools, chars, DateTimes, etc.)
The following data is stored on the heap:

The content of reference-type objects.
Anything structured inside a reference-type object.
