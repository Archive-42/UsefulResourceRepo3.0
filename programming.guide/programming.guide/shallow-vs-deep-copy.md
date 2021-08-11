



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Shallow vs Deep Copy (with examples)

- A shallow copy shares its children with the original
- A deep copy has its own copies of the children

Car make: BMW engine: gearbox: Gearbox gears: 6 Engine cylinders: 12 Shallow copy of Car object Car make: BMW engine: gearbox:

Car make: BMW engine: gearbox: Gearbox gears: 6 Engine cylinders: 12 Deep copy of Car object Car make: BMW engine: gearbox: Gearbox gears: 6 Engine cylinders: 12

## Arrays

The above example showed an object graph. Same story for arrays.

Shallow copy of array Person age: 30

Person age: 30 Deep copy of array Person age: 30

## If there are no children?

Since the concept of deep vs shallow concerns treatment of children, it’s meaningless to talk about deep vs shallow copying of objects (or arrays) that doesn’t have any children. When creating a copy of an array of integers for example, the copy can be seen as both shallow (no children were copied) and deep (all children were copied).

## What about `pointerA = pointerB`?

When you do `pointerA = pointerB` no object is copied, so it’s neither a deep nor a shallow copy. A pointer value _is_ copied but the value itself (the _address_) can’t possibly have any children so it doesn’t make sense to try to categorize this copying as shallow or deep.

## Mixed copies

Mixed copies are part shallow, part deep. If you for instance make shallow copies of the immediate children, then the original and the copy may share the same grand children. You could say that the copying is _one level deep_.

Another type of mixed copy would be if you create copies of some children, while sharing others. If you for example have a reference to a singleton, or an immutable object it doesn’t make sense to clone these objects.

## When to use which?

This has to be decided on a case by case basis. Here are a few pro’s and con’s of each approach to help you decide.

- Shallow copies are easier to implement since they don’t require traversal of the object tree.

- If the data structure to be copied can have cycles, a deep copy implementation needs to keep track of already copied objects to avoid infinite copying.

- If the data structure to be copied is immutable, there’s no risk in sharing state and shallow copies are therefore typically preferred.

- If the data structure is mutable, sharing data could lead to complex code. For this reason deep copies may be preferred. There’s also a middle way, where shallow copies are used until the children are modified, at which point they are copied. This “lazy deep copying” is called copy on write.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
