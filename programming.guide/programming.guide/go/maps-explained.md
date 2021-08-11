<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Hash Tables](../hash-tables.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Amortized time complexity](../amortized-time-complexity-analysis.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  Maps explained
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

# Go: Maps explained

A map is an **unordered** collection of **key-value** pairs, where each key is **unique**.

## Basics

    m := make(map[string]float64)

    m["pi"] = 3.1416

    fmt.Println(m) // "map[pi:3.1416]"

    v1 := m["pi"]  // v1 == 3.1416
    v2 := m["foo"] // v2 == zero value

    _, exists := m["pi"] // exists == true

    if x, ok := m["pi"]; ok {
            fmt.Println(x) // "3.1416"
    }

    delete(m, "pi")
    fmt.Println(m) // "map[]"

- The default zero value of a map is `nil`. A nil map is equivalent to an empty map except that no elements may be added.
- Use `make(mapType, n)` to preallocate room for `n` entries.

## Literals

    m := map[string]float64{
            "e":  2.71828,
            "pi": 3.1416,
    }

## Size

    n := len(m) // n == number of elements in m

## Iteration

    for key, value := range m {
            fmt.Println(key, ": ", value)
    }

- Iteration order is not specified and may vary from iteration to iteration.
- If an entry that has not yet been reached is removed during iteration, the corresponding iteration value will not be produced.
- If an entry is created during iteration, that entry may or may not be produced during the iteration.

## Implementation

- Maps are backed by [hash tables](../hash-tables.html).
- They provide lookup, insert, and delete operations in **constant** [amortized time](../amortized-time-complexity-analysis.html).
- The comparison operators `==` and `!=` must be defined for the key type.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
