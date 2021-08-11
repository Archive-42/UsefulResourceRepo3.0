



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

# Go: Type assertions and type switches

A **type assertion** provides access to an interface's concrete value.

The type assertion `x.(T)` asserts that the concrete value stored in `x` is of type `T`, and that `x` is not nil. More precisely:

- If `T` is not an interface, it asserts that the dynamic type of `x` is identical to `T`.
- If `T` is an interface, it asserts that the dynamic type of `x` implements `T`.

<!-- -->

    var x interface{} = "foo"

    var s string = x.(string)
    fmt.Println(s)     // "foo"

    s, ok := x.(string)
    fmt.Println(s, ok) // "foo true"

    n, ok := x.(int)
    fmt.Println(n, ok) // "0 false"

    n = x.(int)        // ILLEGAL

    panic: interface conversion: interface {} is string, not int

A **type switch** performs several type assertions in series and runs the first case with a matching type:

    var x interface{} = "foo"

    switch v := x.(type) {
    case nil:
            fmt.Println("x is nil")            // here v has type interface{}
    case int:
            fmt.Println("x is", v)             // here v has type int
    case bool, string:
            fmt.Println("x is bool or string") // here v has type interface{}
    default:
            fmt.Println("type unknown")        // here v has type interface{}
    }

    x is bool or string

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
