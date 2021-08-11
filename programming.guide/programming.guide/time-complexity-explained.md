<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Amortized time complexity](amortized-time-complexity-analysis.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Big O notation explained](big-o-notation-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

Time complexity explained
=========================

Time complexity estimates the time to run an algorithm. It's calculated by counting **elementary operations**.

-   [Example](time-complexity-explained.html#example)
-   [Worst-case time](time-complexity-explained.html#worst-case-time)
-   [Average-case time](time-complexity-explained.html#average-case-time)
-   [Linear vs. quadratic time](time-complexity-explained.html#linear-vs-quadratic-time)

Example
-------

What's the running time of the following algorithm?

    Algorithm max(arr):
       max ← arr[0]
       for i = 1 to len(arr)-1
           if arr[i] > max
                max ← arr[i]
       return max

The answer depends on factors such as input, programming language and runtime, coding skill, compiler, operating system, and hardware.

We often want to reason about **execution time** in a way that depends only on the **algorithm** and its **input**. This can be achieved by choosing an **elementary operation**, which the algorithm performs repeatedly, and define the **time complexity** T(*n*) as the number of such operations the algorithm performs given an array of length *n*.

For the algorithm above we can choose the comparison `arr[i] > max` as an elementary operation.

1.  This captures the running time of the algorithm well, since comparisons dominate all other operations in this particular algorithm.
2.  Also, the time to perform a comparison is constant: it doesn't depend on the size of `arr`.

The time complexity, measured in the number of comparisons, then becomes T(*n*) = *n* - 1.

In general, an **elementary operation** must have two properties:

1.  There can't be any other operations that are performed more frequently as the size of the input grows.
2.  The time to execute an elementary operation must be constant: it mustn't increase as the size of the input grows.

Worst-case time
---------------

Consider this algorithm:

    Algorithm contains(arr, x):
       for i = 0 to len(arr)-1
           if x == arr[i]
                return true
       return false

The comparison `x == arr[i]` can be used as an elementary operation in this case. However, for this algorithm the number of comparisons depends not only on the number of elements, *n*, in the array but also on the value of `x` and the values in `arr`:

-   If `x` isn't found in `arr` the algorithm makes *n* comparisons,
-   but if `x` equals `arr[0]` there is only one comparison.

Because of this, we often choose to study **worst-case** time complexity:

-   Let T<sub>1</sub>(*n*), T<sub>2</sub>(*n*), … be the execution times for all possible inputs of size *n*.
-   The worst-cast time complexity W(*n*) is then defined as W(*n*) = max(T<sub>1</sub>(*n*), T<sub>2</sub>(*n*), …).

The worst-cast time complexity for the `contains` algorithm thus becomes W(*n*) = *n*.

Worst-case time complexity gives an upper bound on time requirements and is often easy to compute. The drawback is that it's often overly pessimistic.

Average-case time
-----------------

**Average-case** time complexity is a less common measure:

-   Let T<sub>1</sub>(*n*), T<sub>2</sub>(*n*), … be the execution times for all possible inputs of size *n*, and let P<sub>1</sub>(*n*), P<sub>2</sub>(*n*), … be the probabilities of these inputs.
-   The average-case time complexity is then defined as P<sub>1</sub>(*n*)T<sub>1</sub>(*n*) + P<sub>2</sub>(*n*)T<sub>2</sub>(*n*) + …

Average-case time is often harder to compute, and it also requires knowledge of how the input is distributed.

Linear vs. quadratic time
-------------------------

Finally, we'll look at an algorithm with poor time complexity.

    Algorithm reverse(arr):
       for i = 1 to len(arr)-1
           x ← arr[i]
           for j = i downto 1
               arr[j] ← arr[j-1]
           arr[0] ← x

We choose the assignment `arr[j] ← arr[j-1]` as elementary operation. Updating an element in an array is a constant-time operation, and the assignment dominates the cost of the algorithm.

The number of elementary operations only depends on *n* in this case, and the time complexity becomes

W(*n*)

 = 1 + 2 + ... + *n* - 1 

 = *n*(*n* - 1)/2 

 = *n<sup>2</sup>*/2 - *n*/2

The quadratic term dominates for large *n*, and we therefore say that this algorithm has **quadratic** time complexity. This means that the algorithm **scales poorly** and can be used **only for small input**: to reverse the elements of an array with 10,000 elements, the algorithm will perform about 50,000,000 assignments.

In this case it's easy to find an algorithm with **linear** time complexity.

    Algorithm reverse(arr):
       for i = 0 to n/2
           swap arr[i] and arr[n-i-1]

This is a **huge improvement** over the previous algorithm: an array with 10,000 elements can now be reversed with only 5,000 swaps, i.e. 10,000 assignments. That's roughly a 5,000-fold speed improvement, and the improvement keeps growing as the the input gets larger.

It's common to use [**Big O notation**](big-o-notation-explained.html) when talking about time complexity. We could then say that the time complexity of the first algorithm is Θ(*n*<sup>2</sup>), and that the improved algorithm has Θ(*n*) time complexity.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
