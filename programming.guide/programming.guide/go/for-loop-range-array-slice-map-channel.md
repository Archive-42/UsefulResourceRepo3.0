



## Related

[For loops explained](for-loop.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Iterator pattern](iterator-generator-pattern.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go gotcha: Can't change entries in range loop](gotcha-change-value-range.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go gotcha: Unexpected values in range loop](gotcha-unexpected-values-range.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[For statements](https://golang.org/ref/spec#For_statements)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

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

# Go: Range loops (for each loops) explained

Range statements iterate over slices, arrays, strings, maps or channels.

- [Basics](for-loop-range-array-slice-map-channel.html#basics)
- [Strings](for-loop-range-array-slice-map-channel.html#strings)
- [Maps](for-loop-range-array-slice-map-channel.html#maps)
- [Channels](for-loop-range-array-slice-map-channel.html#channels)

## Basics

    a := []string{"Foo", "Bar"}
    for i, s := range a {
            fmt.Println(i, s)
    }

    0 Foo
    1 Bar

- The range expression, `a`, is **evaluated once** before beginning the loop.
- The iteration values are assigned to the respective iteration variables, `i` and `s`, **as in an assignment statement**.
- The second iteration variable is optional.
- If a slice or map is `nil`, the number of iterations is 0.

## Strings

For a string, the loop iterates over Unicode code points.

    for i, ch := range "日本語" {
            fmt.Printf("%#U starts at byte position %d\n", ch, i)
    }

    U+65E5 '日' starts at byte position 0
    U+672C '本' starts at byte position 3
    U+8A9E '語' starts at byte position 6

- The index is the first byte of a UTF-8-encoded code point; the second value, of type `rune`, is the value of the code point.
- For an invalid UTF-8 sequence, the second value will be 0xFFFD, and the iteration will advance a single byte.

## Maps

The iteration order over maps is not specified and is not guaranteed to be the same from one iteration to the next.

    m := map[string]int{
            "one":   1,
            "two":   2,
            "three": 3,
    }
    for k, v := range m {
            fmt.Println(k, v)
    }

    two 2
    three 3
    one 1

- If a map entry that has not yet been reached is removed during iteration, this value will not be produced.
- If a map entry is created during iteration, that entry may or may not be produced.

## Channels

For channels, the iteration values are the successive values sent on the channel until closed.

    ch := make(chan int)
    go func() {
            ch <- 1
            ch <- 2
            ch <- 3
            close(ch)
    }()
    for n := range ch {
            fmt.Println(n)
    }

    1
    2
    3

For a `nil` channel, the range loop blocks forever.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
