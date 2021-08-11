



## Related

[Time complexity explained](time-complexity-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Big O notation explained](big-o-notation-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go: Append function explained](go/append-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Amortized time complexity

Amortized analysis is used for algorithms that have **expensive operations** that happen **rarely**.

**Amortized complexity analysis** is most commonly used with data structures, which have state that persists between operations. The basic idea is that an expensive operation can alter the state so that the worst case cannot occur again for a long time, thus amortizing its cost.

**Definition:** Let T<sub>1</sub>, T<sub>2</sub>, …, T<sub>k</sub> be the complexities of a sequence of operations on a data structuture. The **amortized complexity** of a single operation in this sequence is (T<sub>1</sub> + T<sub>2</sub> + …+ T<sub>k</sub>) / k.

## Example

    Algorithm append(arr, x):
        if arr.size == arr.capacity
            arr.capacity ← 2 * arr.capacity
            resize arr
        arr[arr.size] ← x
        arr.size ← arr.size + 1

Let's start by looking at the worst case:

The worst-case time complexity for appending an element to an array of length *n* using this algorithm is Θ(_n_):

- if the array is full, the algorithm allocates a new array of length 2*n*,
- and then copies the elements from the old array into the new one.

Cleary, this result is overly pessimistic. The following *n* append operations will be much cheaper: each of them will run in constant time since the newly allocated array has room for all of the new elements.

An amortized time analysis gives a better understanding of the algorithm:

Consider a sequence of *n* append operations, where we start with an array of length 1. A careful analysis shows that the total time of these operations is only Θ(_n_):

- There will be a total of _n_ constant-time assignment and increment operations.
- The resizing will happen only at operation 1, 2, 4, …, 2<sup>k</sup>, for a total of 1 + 2 + 4 + …+ 2<sup>k</sup> = 2·2<sup>k</sup> - 1 constant-time element copy operations. Since 2<sup>k</sup> ≤ *n*, this is at most 2*n* - 1.

Hence, the amortized time complexity for a single append operation is Θ(1).

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
