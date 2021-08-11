<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Interfaces explained](interfaces-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Pointer vs. value receiver](pointer-vs-value-receiver.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Public vs. private](public-private.html)  
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

Go: Methods explained
=====================

Any type declared in a type definition can have methods attached.

    type MyType struct {
            n int
    }

    func (p *MyType) Value() int { return p.n }

    func main() {
            pm := new(MyType)
            fmt.Println(pm.Value()) // Output: 0
    }

This declares a method `Value` associated with `MyType`. In this case, the receiver is named `p` in the body of the function.

You may define methods on any type declared in a type definition. If you convert the value to a different type, the new value will have the methods of the new type, not those of the old type.

    type MyInt int

    func (m MyInt) Positive() bool { return m > 0 }

    func main() {
            var m MyInt = 2
            m = m * m // The operators of the underlying type still apply.

            fmt.Println(m.Positive())         // Output: true
            fmt.Println(MyInt(-1).Positive()) // Output: false

            var n int
            n = int(m) // The conversion is required.
            n = m      // ILLEGAL
    }

    ../main.go:14:4: cannot use m (type MyInt) as type int in assignment

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
