<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Go gotcha
---------

1.  [Why can't I add elements to my map?](gotcha-assignment-entry-nil-map.html)
2.  [What's a nil pointer dereference?](gotcha-nil-pointer-dereference.html)
3.  [Multiple values in single value context?](gotcha-multiple-value-sinlge-value-context.html)
4.  Why doesn't this function change my array?
5.  [Two variables with the same name?](gotcha-shadowing-variables.html)
6.  [Extra comma in slice literal](gotcha-missing-comma-slice-array-map-literal.html)
7.  [Why can't I update my string?](gotcha-strings-are-immutable.html)
8.  [Why aren't the characters concatenated?](gotcha-concatenate-rune-string.html)
9.  [What happened to ABBA?](gotcha-trim-string.html)
10. [What happened to my copy?](gotcha-copy-missing.html)
11. [Why doesn't append work every time?](gotcha-append.html)
12. [Why can't I print large numbers? (constant overflows int)](gotcha-constant-overflows-int.html)
13. [Why doesn't increment (++) and decrement (--) work?](gotcha-increment-decrement-statement.html)
14. [Why is my computation wrong?](gotcha-operator-precedence.html)
15. [Why does Go and Pythagoras disagree?](gotcha-bitwise-operators.html)
16. [Why doesn't this loop end?](gotcha-integer-overflow-wrap-around.html)
17. [Numbers that start with zero](gotcha-octal-decimal-hexadecimal-literal.html)
18. [What's wrong with the remainder (modulo) operator?](gotcha-remainder-modulo-operator.html)
19. [Why can't I multiply a time.Duration with an integer?](gotcha-multiply-duration-integer.html)
20. [Why is this index out of range?](gotcha-index-out-of-range.html)
21. [Unexpected values in range loop](gotcha-unexpected-values-range.html)
22. [Can't change entries in range loop](gotcha-change-value-range.html)
23. [Iteration variable doesn't see change in range loop](gotcha-range-copy-array.html)
24. [Iteration variables and closures](gotcha-data-race-closure.html)
25. [Why is the JSON output empty?](gotcha-json-marshal-empty.html)
26. [Why is nil not equal to nil?](gotcha-why-nil-error-not-equal-nil.html)

<span class="underline"></span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [Go: String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Go: Maps explained](maps-explained.html)
4.  [Go: For loops explained](for-loop.html)
5.  [Go: Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go gotcha: Why doesn't this function change my array?
=====================================================

    func Foo(a [2]int) {
            a[0] = 8
    }

    func main() {
            a := [2]int{1, 2}
            Foo(a)         // Try to change 'a'
            fmt.Println(a) // Output: [1 2]
            
    }

Answer

-   Arrays in Go are **values**.
-   When you pass an array to a function, the array is copied.

If you want `Foo` to update the elements of its argument `a`, **use a slice instead**:

    func Foo(a []int) {
            if len(a) > 0 {
                    a[0] = 8
            }
    }

    func main() {
            a := []int{1, 2}
            Foo(a)         // Change 'a'
            fmt.Println(a) // Output: [8 2]
    }

A slice does not store any data, it just describes a section of an underlying array. Changing the elements of a slice modifies the corresponding elements of its underlying array. Other slices that share the same underlying array will see those changes. <a href="https://tour.golang.org/moretypes/8" class="quote-source">A Tour of Go: Slices</a>

See [Slices explained](slices-explained.html) for all about slices in Go.

<a href="gotcha-multiple-value-sinlge-value-context.html" class="prev"></a>

« Prev

Multiple values in single value context?

[](go-gotcha.html#toc)

TOC

Go gotcha

4 of 26

<a href="gotcha-shadowing-variables.html" class="next"></a>

Next »

Two variables with the same name?

Comments (1)
------------

![User avatar](https://www.gravatar.com/avatar/26d5024db3f1a78d0222162ae91bc21d?d=mp)

Or you can use a pointer to the array, as in

func Foo(a \*\[2\]int) { a\[0\] = 8 }

<span style="color: grey">by Krish | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
