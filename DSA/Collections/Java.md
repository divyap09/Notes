# Java Collections

Java Collections are a set of generic interfaces that describe the most common forms of data structure.

The Java Collections define two fundamental types of data structures:
<ol>
  <li>Collection is a grouping of objects, java.util.Collection </li>
  <li>Map, a set of mappings, or associations, between objects, java.util.Map </li>
</ol>



to find out all the methods in the class:
```
use javap package.filename.class_name
```


Collection are:
<ul>
  <li>List</li>
  <ol>
    <li>ArrayList</li>
    <li>LinkedList</li>
    <li>Vector</li>
  </ol>
  <li>Set</li>
  <ol>
    <li>HashSet</li>
    <li>SortedSet</li>
    <li>TreeSet</li>
  </ol>
</ul>




Maps are:
<ul>
  <li>HashMap</li>
  <li>WeakHashMap</li>
  <li>Hashtable</li>
  <li>SortedMap</li>
    <ol>
      <li>TreeMap</li>
    </ol>
</ul>


Note: 
- SortedMap and SortedSet maintain their elements in sorted order.
- Above mentioned are all interfaces, derived from the package java.util

## Methods are defined for:

1. adding objects
2. removing objects
3. testing an object
4. iterating through all elements
5. return the elements of the group as an array
6. return the size of the collection.


## List Interface:
- child interface of Collection
- it stores ordered collection of objects
- it allows duplicates
- it is implemented through various classes like ArrayList, Stack, Vector.
- so we can instantiate a list object with above classes.


## ArrayList:

- it provides dynamic arrays in Java.
- the size of the arraylist increases when objects are added and shrinks when objects are removed.
- we can randomly access the list
- it uses wrapper classes for the primitive data types.
- objects are not stored in contagious location but the memory is stored in contagious memory.
- it is non-synchronized, can't be shared between many thread, not safe.


## LinkedList:

- linear data structures
- elements are not stored in a contagious location
- every element is a separate object with a data part and address part. they are called nodes
- elements are linked through pointers and addresses.


## Vector:

- similar to ArrayList.
- it is synchronized, can be shared with many threads and it is safe.

## Stack:

- last in first out (LIFO)
- performs operations like,
- push (to insert elements)
- pop (to remove elements)
- search (to find the element in the stack)
- empty (whether stack is empty or not)
- peek (to find the topmost element)
- it is subclass of Vector
- for faster implementation we use ArrayDequeue, which is not thread safe.


## Queue interface:

- implements First In First Out (FIFO)
- order of the elements matter.
- we can instantiate a queue using PriorityQueue, ArrayDequeue.

## Set Interface:

- it doesn't allow duplicates
- impose no ordering on the elements of the set but ordered sets are not prohibited
- it is instantiated with the classes HashSet, LinkedHashSet, and TreeSet.

## HashSet:

- objects are inserted according to their hash code.
- allows insertion of NULL elements.

## LinkedHashSet:

- similar to HashSet
- uses doubly linkedlist to store the data and retaining the order of the elements.

## SortedSet interface:

- it has extra methods to maintain the order
- TreeSet implements this.
- TreeSet uses natural ordering unless any comparator provided explicitly.


## Map interface:

- supports mapping of key-value pairs.
- doesn't support duplicate keys
- we perform operations based on the key

## HashMap:

HashMap uses a technique called Hashing. Hashing is a technique of converting a large String to small String that represents the same String so that the indexing and search operations are faster.

## LinkedHashMap:

same as HashMap but maintains the insertion order.

## SortedMap:

it doesn't allow null keys or null values.

TreeMap cannot have null keys but can have null values.
