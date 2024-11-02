# OOPs, Object-Oriented Programming System.

- a language that uses objects.
- bottom-up approach
- it lets us add new methods without compromising data security.
- it lets us create working methods and variables, then re-use all or part of them without compromising security. Code reusability and code optimization.
- it binds data members and member functions together and only performs necessary actions to access the code.

## Object:
- a runtime entity. Member functions are accessed through the objects.
- it has state (attributes), behavior (methods), and identity(name).
- it can be either physical or logical.
- an object is a value that you can manipulate by calling one or more of its methods.
- objects are stored in heap memory, will be removed by JVM by using a garbage collector when there are no more reference counts are there.

### The difference between Stack and Heap memory is:

Heap memory is used by all the parts of the application, whereas stack memory is used only by one thread of execution. Whenever an object is created, it’s always stored in the Heap space and stack memory contains the reference to it.

### Creation of object:

The process of creating a new object is called Construction.

```
Classname object;   //it contains null, if try to use it will result in compile-error

Classname object = new Classname(with or without parameters); //holds the memory address of the class
```

**new** –  to dynamically allocate memory for an object and returns a reference to it.

### Assigning objects:
```
Student b1= new Student();

Student b2=b1;
```

- both are accessing the same memory and both refer to the same object.
- it’s like making a copy of a reference.
- changes made in b2 will affect b1 and vice-versa.

but if,
```
b1=null;
```

Here, the reference to the memory will be removed for object b1. But still, b2 refers to the original object.

### Deleting an object:

Either remove the reference by assigning it to null or after leaving the block when it is no longer needed garbage collector will delete it.


## Class:

- it is the blueprint from which the objects and member functions are created.
- it creates a new data type that can be used to create objects.
- only an object has memory space but a class doesn’t.
- the best practise of naming a class is, the first character should be capital.

Instance variables – data or variables defined within a class

Syntax:
```
<access-modifier> class <class name>{

//instance variables
//constructors
//getter and setter methods
//blocks
//nested classes

}
```

## Constructor :

- It is used to initialize the objects
- It should have the same name as the class name
- It should not have any return type
- It should not be static, final, or abstract.
- It executes immediately when an object is initialized.


1. Getter or Accessor method: a method that accesses an object and returns some information about it, without changing the object.
2. Setter or Mutator method: a method whose purpose is to modify the internal data of an object.

“this” keyword referes to the current object.

“super” keyword refers to the parent class constructor, methods.


## Inheritance:

– acquiring properties and behavior from the parent class to the child class.
– it provides code reusability.
– to achieve runtime polymorphism (method overriding)


### Types of inheritance
1. Single inheritance
2. Multilevel inheritance
3. Hierarchical inheritance
4. Hybrid inheritance

– Multiple inheritance is achieved through interfaces because java doesn’t support it.

We use the “extends” keyword to inherit from parent class to child class.

## Abstraction:

- Identifying the only required characteristics, ignoring the non-essential elements.
- implementation hiding
- it can be achieved through
  1. abstract class (0% to 100%)
  2. interfaces (100%)


## Abstract Class:

- A method without a body is known as an Abstract method.
- if a method is an abstract method it should be an abstract class or not in vice-versa.
- all abstract methods needed to be implemented when a class extends an abstract class. Or else it throws an error.
- they cannot be instantiated, we can’t create objects to an abstract class

## Interface:

- Interfaces cannot be instantiated—they can only be implemented by classes or extended by other interfaces.
- It supports multiple inheritance.
- it used to achieve loose coupling( more independency and easier to maintain)
- it should have only abstract methods or static methods.
- it has a public static final before its instance variables.

contain only constants, method signatures, default methods, static methods, and nested types. Method bodies exist only for default methods and static methods.

## Encapsulation:

- Wrapping up data and methods into a single unit.
- data hiding
- it hides the data through access specifiers.

This is the practice of keeping fields within a class private, then providing access to them via public methods i.e getters and setters.

## Polymorphism:

– to execute in multiple forms

1. Overriding
2. Overloading
