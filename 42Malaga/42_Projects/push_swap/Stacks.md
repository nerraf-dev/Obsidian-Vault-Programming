## What is a stack?
A linear data structure that follows a last in, first out (LIFO) principle. So the last element to be added to the stack will be the first one to be removed. Think of it like a pile of papers or stack of plates. Imagine putting the dishes away, you pick up the plate and put it in its place in the cupboard, you get the next one and place that on top, and then the same with the next. Someone comes in and wants a plate for their cake, so they take the top plate, which is the one you've just put in. 

There are some basic operations that are carried out on stacks:

- `Push`: Adds a new element to the top of the stack.
- `Pop`: Removes the top element from the stack.
- `Peek` (or Top): Returns the top element of the stack without removing it.
- `IsEmpty`: Checks if the stack is empty.
- `IsFull`: Checks if the stack is full (in the case of an array-based implementation)
![[Pasted image 20240913093250.png]]

Stacks can be implemented using methods such as arrays and linked lists.

An [[Example in C using arrays]].

One issue I see with the array method straight away is that it needs to be defined with a size. In the `push_swap` program a number of integers are passed as arguments to be stored to the stack and so the array can not have a fixed length, it could be 3 or 500. 


