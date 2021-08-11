## Further Reading

[Variadic functions (...T)](variadic-function.html)  
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

# Go: Pass a slice to a variadic function

You can pass a slice `s` directly to a variadic funtion using the `s...` notation.

    func main() {
            primes := []int{2, 3, 5, 7}
            fmt.Println(Sum(primes...)) // 17
    }

    func Sum(nums ...int) int {
            res := 0
            for _, n := range nums {
                    res += n
            }
            return res
    }

The `...` syntax can't be applied directly to an array. You must use an intermediate slice:

    fmt.Println(Sum(myArray[:]...))

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
