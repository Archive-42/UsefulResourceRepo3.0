



## Further Reading

[Interfaces explained](interfaces-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: The empty interface

The **empty interface** in Go corresponds to a void pointer in C or an Object reference in Java. It specifies zero methods:

    interface{}

A variable of empty interface type can hold values of any type since every type implements at least zero methods:

    var a interface{}

    a = 24
    fmt.Printf("[%v, %T]\n", a, a) // "[24, int]"

    a = &Point{1, 2}
    fmt.Printf("[%v, %T]\n", a, a) // "[(1,2), *main.Point]"

The [`fmt.Println`](https://golang.org/pkg/fmt/#Println) function is a chief example from the standard library. It takes any number of arguments of any type:

    func Println(a ...interface{}) (n int, err error)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
