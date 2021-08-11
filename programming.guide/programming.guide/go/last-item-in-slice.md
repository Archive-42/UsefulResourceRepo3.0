<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Delete an element from a slice](delete-element-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Clear a slice](clear-slice.html)  
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

Go: Last item in slice
======================

To read the last element:

    a := []string{"A", "B", "C"}
    s := a[len(a)-1] // C

To remove it:

    a = a[:len(a)-1] // [A B]

(Go doesn't have negative indexing like Python does.)

Watch out for memory leaks
--------------------------

If the slice is permanent and the element temporary, you may want to remove the reference before removing the element from the slice:

    a[len(a)-1] = "" // write zero value to avoid memory leak
    a = a[:len(a)-1] // [A B]

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
