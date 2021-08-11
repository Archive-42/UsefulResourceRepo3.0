<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Round float to integer value](round-float-to-int.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The trouble with rounding floating point numbers](https://www.theregister.co.uk/2006/08/12/floating_point_approximation/)  
<span style="color: grey; font-style: italic; font-size: smaller">The Register</span>

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

Go: Round float to 2 decimal places
===================================

String
------

To display the value as a string, use the [`fmt.Sprintf`](https://golang.org/pkg/fmt/#Sprintf) method.

    s := fmt.Sprintf("%.2f", 12.3456) // s == "12.35"

The [Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html) lists the most common formatting verbs and flags.

Float
-----

To round to a floating-point value, use one of these techniques:

    f := 12.3456
    fmt.Println(math.Floor(f*100)/100, // 12.34 (round down)
            math.Round(f*100)/100,     // 12.35 (round to nearest)
            math.Ceil(f*100)/100)      // 12.35 (round up)

Due to the quirks of floating point representation, these rounded values may be slightly off.

The [`math.Round`](https://tip.golang.org/pkg/math/#Round) function will be introduced in Go 1.10. The article [Round float to nearest int](round-float-to-int.html) contains equivalent code.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
