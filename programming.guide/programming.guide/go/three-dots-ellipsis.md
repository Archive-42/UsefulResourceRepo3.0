<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Variadic functions (...T)](variadic-function.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Description of package lists](https://golang.org/cmd/go/#hdr-Description_of_package_lists)  
<span style="color: grey; font-style: italic; font-size: smaller">Command go</span>

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

# Go: Three dots (ellipsis) notation

The three dots `...` notation is used in four different places in Go:

- [Variadic function parameters](three-dots-ellipsis.html#variadic-function-parameters)
- [Arguments to variadic functions](three-dots-ellipsis.html#arguments-to-variadic-functions)
- [Array literals](three-dots-ellipsis.html#array-literals)
- [The go command](three-dots-ellipsis.html#the-go-command)

## Variadic function parameters

If the **last parameter** of a function has type `...T`, it can be called with any number of trailing arguments of type `T`.

The actual type of `...T` inside the function is `[]T`.

**Example:** This function can be called with for instance `Sum(1, 2, 3)` or `Sum()`.

    func Sum(nums ...int) int {
            res := 0
            for _, n := range nums {
                    res += n
            }
            return res
    }

## Arguments to variadic functions

You can pass a slice `s` directly to a variadic funtion by "unpacking" it using the `s...` notation. In this case no new slice is created.

**Example:** Passing a slice to the `Sum` function:

    primes := []int{2, 3, 5, 7}
    fmt.Println(Sum(primes...)) // 17

## Array literals

In an array literal, the `...` notation specifies a length equal to the number of elements in the literal.

**Example:** Array literal with length inferred:

    stooges := [...]string{"Moe", "Larry", "Curly"}
    // len(stooges) == 3

## The go command

Three dots are used by the [`go`](https://golang.org/cmd/go/) command as a wildcard when describing package lists.

**Example:** Tests all packages in the current directory and its subdirectories:

    $ go test ./...

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
