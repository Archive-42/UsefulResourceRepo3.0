<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Type assertions and type switches](type-assertion-switch.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Recover from a panic](recover-from-panic.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The Laws of Reflection](https://blog.golang.org/laws-of-reflection)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

Go: Find the type of an object
==============================

A simple string
---------------

Use the `%T` flag in the [fmt](https://golang.org/pkg/fmt/) package to get a Go-syntax representation of the type.

    var x interface{} = []int{1, 2, 3}
    xType := fmt.Sprintf("%T", x)
    fmt.Println(xType)
    // Output: []int

A simple choice
---------------

Use a type switch to do several type assertions in series.

    var x interface{} = 2.3
    switch v := x.(type) {
    case int:
            fmt.Println("int:", v)
    case float64:
            fmt.Println("float64:", v)
    default:
            fmt.Println("unknown")
    }
    // Output: float64: 2.3

Full type information
---------------------

Use the [reflect](https://golang.org/pkg/reflect/) package if the options above don't suffice.

    var x interface{} = []int{1, 2, 3}
    xType := reflect.TypeOf(x)
    xValue := reflect.ValueOf(x)
    fmt.Println(xType, xValue)
    // Output: []int [1 2 3] 

In this advanced example, we use reflection to check if a list of interface variables have types corresponding to the parameters of a given function. If so, we call the function with those parameters to check if there is a panic.

    // Panics tells if function f panics with parameters p.
    func Panics(f interface{}, p ...interface{}) bool {
            fv := reflect.ValueOf(f)
            ft := reflect.TypeOf(f)
            if ft.NumIn() != len(p) {
                    panic("wrong argument count")
            }
            pv := make([]reflect.Value, len(p))
            for i, v := range p {
                    if reflect.TypeOf(v) != ft.In(i) {
                            panic("wrong argument type")
                    }
                    pv[i] = reflect.ValueOf(v)
            }
            return call(fv, pv)
    }

    func call(fv reflect.Value, pv []reflect.Value) (b bool) {
            defer func() {
                    if err := recover(); err != nil {
                            b = true
                    }
            }()
            fv.Call(pv)
            return
    }

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
