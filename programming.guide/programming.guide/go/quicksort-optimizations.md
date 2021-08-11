<span class="underline"></span>

<span class="underline"></span>

Related
-------

[How to sort in Go](how-to-sort-in-go.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Top 3 Quicksort optimizations
=============================

Most Quicksort optimizations give only small improvements. Here are the ones that make a real difference.

-   Choose a good pivot,
-   use 3-way partitioning,
-   switch to a simpler algorithm for short sublists.

Algorithm overview
------------------

-   Pick an element `p`, called a pivot, from the list.
-   Partition the list so that
    -   all elements less than `p` come first,
    -   all elements greater than `p` come last,
    -   elements equal to `p` go into the middle.
-   Recursively apply the above steps to the sublists of small and large elements.
-   For short sublists, use a simpler sorting algorithm.

<!-- -->

    //  Quicksort sorts the elements of v in ascending order.
    func Quicksort(v []int) {
            if len(v) < 20 {
                    InsertionSort(v)
                    return
            }
            p := Pivot(v)
            low, high := Partition(v, p)
            Quicksort(v[:low])
            Quicksort(v[high:])
    }

With some ingenuity this algorithm can be implemented to run very fast.

If we assume that the partition is done in linear time (which is possible to achieve) and that the list is divided exactly in the middle (which is unlikely), the expected time to sort a list of *n* elements is <span class="no-wrap">*O*(*n* log(*n*))</span>.

Unfortunately the worst case is θ(*n*<sup>2</sup>), but this case is rare if the pivot is chosen carefully.

Pivot
-----

Choosing a suitable pivot `p` is a balancing act:

-   if we are sloppy, the partition can be lopsided;
-   if we compute `p` as the median of all elements, this step may dominate the running time.

A simple solution is to choose `p` as a random list element. The expected number of comparisons for sorting a list of elements, all different, then becomes <span class="no-wrap">1.4 *n* log(*n*)</span>. Also, with a good random source, this choice virtually eliminates the risk of quadratic performance.

Another common choice is `p := Median(v[0], v[len(v)/2], v[len(v)-1])`, but this can be risky. In fact, combining this pivot with the partion algorithm in the next section gives very poor performance when sorting an already sorted list.

A more robust solution is to combine the two ideas and use the median of three random elements. With this strategy, the expected number of comparisons becomes <span class="no-wrap">1.2 *n* log(*n*)</span>.

    func Pivot(v []int) int {
            n := len(v)
            return Median(v[rand.Intn(n)], v[rand.Intn(n)], v[rand.Intn(n)])
    }

    func Median(a, b, c int) int {
            if a < b {
                    switch {
                    case b < c:
                            return b
                    case a < c:
                            return c
                    default:
                            return a
                    }
            }
            switch {
            case a < c:
                    return a
            case b < c:
                    return c
            default:
                    return b
            }
    }

3-way partition
---------------

This 3-way partition algorithm handles input with many replicated elements gracefully, a case where the standard 2-way partition can run into troubles. A well-chosen loop invariant is vital if we want to untangle this intricate piece of code.

    // Partition reorders the elements of v so that:
    // - all elements in v[:low] are less than p,
    // - all elements in v[low:high] are equal to p,
    // - all elements in v[high:] are greater than p.
    func Partition(v []int, p int) (low, high int) {
            low, high = 0, len(v)
            for mid := 0; mid < high; {
                    // Invariant:
                    //  - v[:low] < p
                    //  - v[low:mid] = p
                    //  - v[mid:high] are unknown
                    //  - v[high:] > p
                    //
                    //         < p       = p        unknown       > p
                    //     -----------------------------------------------
                    // v: |          |          |a            |           |
                    //     -----------------------------------------------
                    //                ^          ^             ^
                    //               low        mid           high
                    switch a := v[mid]; {
                    case a < p:
                            v[mid] = v[low]
                            v[low] = a
                            low++
                            mid++
                    case a == p:
                            mid++
                    default: // a > p
                            v[mid] = v[high-1]
                            v[high-1] = a
                            high--
                    }
            }
            return
    }

It's easy to see that the algorithm runs in linear time: the distance between `mid` and `high` decreases in every loop, either because `mid` increases or because `high` decreases.

Combining algorithms
--------------------

Experience shows that Quicksort is the fastest comparison-based sorting algorithm for many types of data. However, in some cases there are better options. Insertion sort, which has quadratic worst-case time, tends to be faster for small lists.

By combining the two algorithms we get the best of two worlds:

-   use Quicksort to sort long sublists,
-   and Insertion sort otherwise.

The optimal break point depends on many factors (how the code is written, the nature of the data, hardware characteristics) and has to be found experimentally. Luckily the choice is seldom critical: break points between 10 and 100 tend to work well.

    func InsertionSort(v []int) {
            for j := 1; j < len(v); j++ {
                    // Invariant: v[:j] contains the same elements as
                    // the original slice v[:j], but in sorted order.
                    key := v[j]
                    i := j - 1
                    for i >= 0 && v[i] > key {
                            v[i+1] = v[i]
                            i--
                    }
                    v[i+1] = key
            }
    }

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
