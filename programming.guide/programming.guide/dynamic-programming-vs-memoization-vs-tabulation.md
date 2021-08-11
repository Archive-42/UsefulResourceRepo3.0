<span class="underline"></span>

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  Dynamic programming vs memoization vs tabulation
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

Dynamic programming vs memoization vs tabulation
================================================

Dynamic programming is a technique for solving problems recursively. It can be implemented by **memoization** or **tabulation**.

Dynamic programming
-------------------

Dynamic programming, DP for short, can be used when the computations of subproblems overlap.

If you’re computing for instance `fib(3)` (the third [Fibonacci number](https://en.wikipedia.org/wiki/Fibonacci_number)), a naive implementation would compute `fib(1)` twice:

fib(3) fib(2) fib(1) fib(0) fib(1)

With a more clever DP implementation, the tree could be collapsed into a graph (a DAG):

fib(3) fib(2) fib(1) fib(0)

It doesn’t look very impressive in this example, but it’s in fact enough to bring down the complexity from *O*(2<sup>*n*</sup>) to *O*(*n*). Here’s a better illustration that compares the full call tree of `fib(7)` (left) to the corresponding collapsed DAG:

-716.40625 fib(1) fib(0) fib(2) fib(1) fib(3) fib(1) fib(0) fib(2) fib(4) fib(1) fib(0) fib(2) fib(1) fib(3) fib(5) fib(1) fib(0) fib(2) fib(1) fib(3) fib(1) fib(0) fib(2) fib(4) fib(6) fib(1) fib(0) fib(2) fib(1) fib(3) fib(1) fib(0) fib(2) fib(4) fib(1) fib(0) fib(2) fib(1) fib(3) fib(5) fib(7) -716.40625 fib(8) fib(7) fib(6) fib(5) fib(4) fib(3) fib(2) fib(1) fib(0)

This improvement in complexity is achieved regardles of which DP technique (memoization or tabulation) is used.

Memoization
-----------

Memoization refers to the technique of caching and reusing previously computed results. Here’s a comparison of a `square` function and the memoized version:

    square(x) {              square_mem(x) {
      return x * x             if (mem[x] is not set)
    }                            mem[x] = x * x
                               return mem[x]
                             }

A memoized `fib` function would thus look like this:

    fib_mem(n) {
        if (mem[n] is not set)
            if (n < 2) result = n
            else result = fib_mem(n-2) + fib_mem(n-1)
            mem[n] = result
        return mem[n]
    }

As you can see `fib_mem(k)` will only be computed **at most once** for each <span class="identifier">k</span>. (Second time around it will return the memoized value.)

This is enough to cause the tree to collapse into a graph as shown in the figures above. For `fib_mem(4)` the calls would be made in the following order:

    fib_mem(4)
        fib_mem(3)
            fib_mem(2)
                fib_mem(1)
                fib_mem(0)
            fib_mem(1)       already computed
        fib_mem(2)           already computed

This approach is **top-down** since the original problem, `fib_mem(4)`, is at the top in the above computation.

Tabulation
----------

Tabulation is similar in the sense that it builds up a cache, but the approach is different. A tabulation algorithm focuses on filling the entries of the cache, until the target value has been reached.

While DP problems, such as the fibonacci computation, are recursive in nature, a tabulation implementation is always iterative.

The tabulation version of `fib` looks like this:

    fib_tab(n) {
        mem[0] = 0
        mem[1] = 1
        for i = 2...n
            mem[i] = mem[i-2] + mem[i-1]
        return mem[n]
    }

The computation of `fib_tab(4)` can be described as follows:

    mem[0] = 0
    mem[1] = 1
    mem[2] = mem[0] + mem[1]
    mem[3] = mem[1] + mem[2]
    mem[4] = mem[2] + mem[3]

As opposed to the memoization technique, this computation is **bottom-up** since original problem, `fib_tab(4)`, is at the bottom of the computation.

**Complexity Bonus:** The complexity of recursive algorithms can be hard to analyze. With a tabulation based implentation however, you get the complexity analysis for free! Tabulation based solutions always boils down to filling in values in a vector (or matrix) using for loops, and each value is typically computed in constant time.

Should I use tabulation or memoization?
---------------------------------------

If the original problem requires all subproblems to be solved, tabulation usually outperformes memoization by a constant factor. This is because tabulation has no overhead for recursion and can use a preallocated array rather than, say, a hash map.

If only some of the subproblems need to be solved for the original problem to be solved, then memoization is preferrable since the subproblems are solved lazily, i.e. precisely the computations that are needed are carried out.

Comments (7)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Great explanation thanks!

<span style="color: grey">by JustMe | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Best explanation you can find! Precise & Concise!

<span style="color: grey">by Anonymous | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/84f8dc6e3c2b5ee51cb0f4511c3b3f34?d=mp)

Could you comment on the memory complexity difference between them, because it could be an important factor to choose between memorization and “tabulation”. Pseudo-tabulation and a bottom-up approach has better memory complexity when we do not need to “remember” all previous solutions. (In Fibonacci for example, only the last 2 values must be remembered)

<span style="color: grey">by Mrio | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

That’s a good point. In the tabulation approach you have more control over what data to save for later. Inside a memoized function it is hard to make a decision on what previous results can be discarded.

I guess the bottom line is this: If you want such finer grained control over memory usage, memoization may not be a viable option.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/20e1d5ff10178d42db044cdf0cb30e97?d=mp)

Could you please comment on the time complexity of both of approaches. Does memoization still take O(2<sup>n</sup>) since we are anyways making the recursive call?

<span style="color: grey">by Abi | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Both algorithms are O(*n*), but I understand your confusion since `fib_mem` is being called more than *n* times. There are however two important things to note:

1.  We are in fact not *always* making the recursive calls. Even if `fib_mem(5)` is called more than once, it will only recurse into `fib_mem(4)` and `fib_mem(3)` the first time it's called.

2.  One must keep in mind what's being analyzed. In algorithms like these, it's typically arithmetic operations, such as number of additions, that's being analyzed. A call to `fib_mem(2)` incurs zero cost if the value has already been computed.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/046bac1bde8fbbab3c30b7ed359af13e?d=mp)

This explanation... It has different kind of simplicity. It reminds me the quote that Einstein once said, "If you can't explain it to a six year old, you don't understand it yourself" Thank you sir :)

<span style="color: grey">by Fatih Keskin | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
