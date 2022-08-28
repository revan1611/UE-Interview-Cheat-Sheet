# Interview Cheat Sheet

### C++ vs C# [Definition](https://csharp-station.com/understanding-the-differences-between-c-c-and-c/)

- C++ is an object-oriented language, C# is considered a component-oriented programming language
- C++ compiles into machine code, while C# compiles to CLR, which is interpreted by ASP.NET
- C++ requires you to handle memory manually, but C# runs in a virtual machine which can automatically handle memory management

### Cast Types
- **const_cast**<type> (expr) − The const_cast operator is used to explicitly override const and/or volatile in a cast. The target type must be the same as the source type except for the alteration of its const or volatile attributes. This type of casting manipulates the const attribute of the passed object, either to be set or removed.

- **dynamic_cast**<type> (expr) − The dynamic_cast performs a runtime cast that verifies the validity of the cast. If the cast cannot be made, the cast fails and the expression evaluates to null. A dynamic_cast performs casts on polymorphic types and can cast a A* pointer into a B* pointer only if the object being pointed to actually is a B object.

- **reinterpret_cast**<type> (expr) − The reinterpret_cast operator changes a pointer to any other type of pointer. It also allows casting from pointer to an integer type and vice versa.

- **static_cast<type>** (expr) − The static_cast operator performs a nonpolymorphic cast. For example, it can be used to cast a base class pointer into a derived class pointer.

### Smart Pointers
A Smart Pointer is a `wrapper class over a pointer with an operator like * and -> overloaded`. The objects of the smart pointer class look like normal pointers. But, unlike Normal Pointers it can deallocate and free destroyed object memory.

**Types of Smart Pointers:**
- **Unique pointer**- unique_ptr stores one pointer only. We can assign a different object by removing the current object from the pointer.
- **Shared Pointer**- By using shared_ptr more than one pointer can point to this one object at a time and it’ll maintain a Reference Counter using use_count() method.
- **Weak pointer**- It’s much more similar to shared_ptr except it’ll not maintain a Reference Counter. In this case, a pointer will not have a stronghold on the object. The reason is if suppose pointers are holding the object and requesting for other objects then they may form a Deadlock.

### UObject [Source](https://docs.unrealengine.com/5.0/en-US/API/Runtime/CoreUObject/UObject/UObject/)

The base class of all UE objects. The type of an object is defined by its UClass. This provides support functions for creating and using objects, and virtual functions that should be overridden in child classes.

### Unreal Object Handling [Source](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ProgrammingWithCPP/UnrealArchitecture/Objects/Optimizations/)

Marking classes, properties, and functions with the appropriate macros turns them into `UClasses`, `UProperties`, and `UFunctions`. This gives Unreal Engine access to them, which allows for a number of under-the-hood handling features to be implemented. 

### Garbage Collection in Unreal Engine [Source](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ProgrammingWithCPP/UnrealArchitecture/Objects/Optimizations/)

Unreal implements a garbage collection scheme whereby UObjects that are no longer referenced or have been explicitly flagged for destruction will be cleaned up at regular intervals. The engine builds a reference graph to determine which UObjects are still in use and which ones are orphaned. At the root of this graph is a set of UObjects designated as the "root set". Any UObject can be added to the root set. When garbage collection occurs, the engine can track all referenced UObjects by searching the tree of known UObject references, starting from the root set. Any unreferenced UObjects, meaning those which are not found in the tree search, will be assumed to be unneeded, and will be removed. 

### Class Default Object (CDO) [Definition](https://forums.unrealengine.com/t/what-is-cdo/310820)

CDO is Class Default Object, it's a master copy of object for specific class contained in reflection system which in this case it's contained in class representing the class which is UClass. CDO contains object defaults and make them accessible very easily since C++ don't have such a feature.

### OOP [Definition](https://www.w3schools.com/cpp/cpp_oop.asp)

Procedural programming is about writing procedures or functions that perform operations on the data, while object-oriented programming is about creating objects that contain both data and functions.

- OOP provides a clear structure for the programs.
- OOP helps to keep the C++ code DRY "Don't Repeat Yourself", and makes the code easier to maintain, modify and debug.
- OOP makes it possible to create full reusable applications with less code and shorter development time.

### Constructor:  [Definition](https://www.mygreatlearning.com/blog/constructor-in-cpp/)

- A constructor in C++ is a special ‘MEMBER FUNCTION’ having the same name as that of its class which is used to initialize some valid values to the data members of an object. It is executed automatically whenever an object of a class is created. The only restriction that applies to the constructor is that it must not have a return type or void. It is because the constructor is automatically called by the compiler and it is normally used to **INITIALIZE VALUES**. The compiler distinguishes the constructor from other member functions of a class by its name which is the same as that of its class. ctorz is an abbreviation of constructor in C++.

### Virtual Function [Definition](https://www.javatpoint.com/cpp-virtual-function)

- A C++ virtual function is a member function in the base class that you redefine in a derived class
- It is used to tell the compiler to perform dynamic linkage or late binding on the function.
- There is a necessity to use the single pointer to refer to all the objects of the different classes.

**Rules of Virtual Function**

- Virtual functions must be members of some class.
- Virtual functions cannot be static members.
- They are accessed through object pointers.
- They can be a friend of another class.
- A virtual function must be defined in the base class, even though it is not used.
- The prototypes of a virtual function of the base class and all the derived classes must be identical. If the two functions with the same name but different prototypes, C++ will consider them as the overloaded functions.
- We cannot have a virtual constructor, but we can have a virtual destructor
- Consider the situation when we don't use the virtual keyword.

**Pure Virtual Function**

- A virtual function is not used for performing any task. It only serves as a placeholder.
- When the function has no definition, such function is known as **"do-nothing"** function.
- The **"do-nothing"** function is known as a **pure virtual function**. A pure virtual function is a function declared in the base class that has no definition relative to the base class.
- A class containing the pure virtual function cannot be used to declare the objects of its own, such classes are known as abstract base classes.
- The main objective of the base class is to provide the traits to the derived classes and to create the base pointer used for achieving the runtime polymorphism.

### Const [Definition]()

- The const keyword specifies that a variable's value is constant and tells the compiler to prevent the programmer from modifying it.
- you can use the const keyword instead of the #define preprocessor directive to define constant values. Values defined with const are subject to type checking, and can be used in place of constant expressions. In C++, you can specify the size of an array with a const variable as follows

### New and Malloc Operator [Definition](https://www.includehelp.com/cpp-tutorial/difference-between-new-and-malloc.aspx)

- new is an operator whereas malloc() is a library function. new allocates memory and calls constructor for object initialization. But malloc() allocates memory and does not call constructor. ... new is faster than malloc() because an operator is always faster than a function.

### Object Slicing [Definition](https://www.geeksforgeeks.org/object-slicing-in-c/)

- Object slicing happens when a derived class object is assigned to a base class object, additional attributes of a derived class object are sliced off to form the base class object.

### Templates [Definition](https://www.cplusplus.com/doc/oldtutorial/templates/)

- Function templates are special functions that can operate with generic types. This allows us to create a function template whose functionality can be adapted to more than one type or class without repeating the entire code for each type.

### Stack and Heap [Definition](https://www.guru99.com/stack-vs-heap.html)

- A stack is a special area of computer’s memory which stores temporary variables created by a function. In stack, variables are declared, stored and initialized during runtime.
- Stack is a temporary storage memory. When the computing task is complete, the memory of the variable will be automatically erased. The stack section mostly contains methods, local variable, and reference variables.
- The heap is a memory used by programming languages to store global variables. By default, all global variable are stored in heap memory space. It supports Dynamic memory allocation.
- The heap is not managed automatically for you and is not as tightly managed by the CPU. It is more like a free-floating region of memory.

### Dot/Cross Product [Definition](https://www.geeksforgeeks.org/program-dot-product-cross-product-two-vector/)

- There are two vector A and B and we have to find the dot product and cross product of two vector array. `Dot product` is also known as `scalar product` and `cross product` also known as `vector product`.

>**Dot Product**
The dot product is a simple yet extremely useful mathematical tool. It encodes the relationship between two vectors' magnitudes and directions into a single value.

>**Cross Product**
The cross product is a mathematical operation applied on two input vectors that returns a perpendicular vector in relation to the two input vectors.

### Unreal Multiplayer [Overview](https://docs.unrealengine.com/4.27/en-US/InteractiveExperiences/Networking/Overview/)

**Network Modes and Server Types**

- ***Standalone***: The game is running as a server that does not accept connections from remote clients. Any players participating in the game are strictly local players. This mode is used for single-player and local multiplayer games. It will run both server-side logic and client-side logic as appropriate for the local players.
- ***Client***: The game is running as a client that is connected to a server in a network multiplayer session. It will not run any server-side logic.
- ***Listen Server***: The game is running as a server hosting a network multiplayer session. It accepts connections from remote clients and has local players directly on the server. This mode is often used for casual cooperative and competitive multiplayer.
- ***Dedicated Server***: The game is running as a server hosting a network multiplayer session. It accepts connections from remote clients, but has no local players, so it discards graphics, sound, input, and other other player-oriented features in order to run more efficiently. This mode is often used for games requiring more persistent, secure, or large-scale multiplayer.

### Unreal Programming Basics [Overview](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ProgrammingWithCPP/IntroductionToCPP/)
