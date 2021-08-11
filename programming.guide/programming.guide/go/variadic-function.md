<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Append function explained](append-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Passing arguments to ... parameters](https://golang.org/ref/spec#Passing_arguments_to_..._parameters)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

[Appending to and copying slices](https://golang.org/ref/spec#Appending_and_copying_slices)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Variadic functions (...T)

If the **last parameter** of a function has type `...T` like this:

    func Sum(nums ...int) int {
            res := 0
            for _, n := range nums {
                    res += n
            }
            return res
    }

...it can be called with **any number** of trailing arguments of type `T`.

    fmt.Println(Sum())        // 0
    fmt.Println(Sum(1, 2, 3)) // 6

The actual type of `...T` inside the function is `[]T`.

You can pass a slice `s` directly to a variadic funtion using the `s...` notation. In this case no new slice is created.

    primes := []int{2, 3, 5, 7}
    fmt.Println(Sum(primes...)) // 17

## Append is variadic

As a special case, you can append a string to a byte slice using the built-in `append` function:

    var buf []byte
    buf = append(buf, 'a', 'b')
    buf = append(buf, "cd"...)
    fmt.Println(buf) // [97 98 99 100]

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
