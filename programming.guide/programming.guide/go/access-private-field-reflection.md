



## Further Reading

[Public vs. private](public-private.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The Laws of Reflection](https://blog.golang.org/laws-of-reflection)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

# Go: Access private fields using reflection

Using reflection, it's possible to read (but not write) unexported fields of a struct defined in another package.

## Example

The `List` struct in package [`container/list`](https://golang.org/pkg/container/list/) has an unexported field `len`:

    package list

    type List struct {
            root Element
            len  int
    }

    …

This code reads the value of `len` using reflection:

    package main

    import (
            "container/list"
            "fmt"
            "reflect"
    )

    func main() {
            l := list.New()
            l.PushFront("foo")
            l.PushFront("bar")

            // Get a reflect.Value fv for the unexported field len.
            fv := reflect.ValueOf(l).Elem().FieldByName("len")
            fmt.Println(fv.Int()) // 2

            // Try to set the value of len.
            fv.Set(reflect.ValueOf(666)) // ILLEGAL
    }

    2
    panic: reflect: reflect.Value.Set using value obtained using unexported field

    goroutine 1 [running]:
    reflect.flag.mustBeAssignable(0x1a2, 0x285a)
            /usr/local/go/src/reflect/value.go:225 +0x280
    reflect.Value.Set(0xee2c0, 0x10444254, 0x1a2, 0xee2c0, 0x1280c0, 0x82)
            /usr/local/go/src/reflect/value.go:1345 +0x40
    main.main()
            ../main.go:18 +0x280

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
