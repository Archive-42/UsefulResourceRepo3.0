



## Further Reading

[Random Generators: What is a seed?](../random-generators-what-is-a-seed.html)  
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

# Go: Generate a random character (rune)

## Between 'a' and 'z'

Use the [`rand.Intn`](https://golang.org/pkg/math/rand/#Intn) function in package [`math/rand`](https://golang.org/pkg/math/rand/).

    rand.Seed(time.Now().UnixNano())
    c := 'a' + rand.Intn(26)

Without the call to `rand.Seed`, a program will produce the same sequence of pseudo-random numbers for each execution.

## From arbitrary set

    chars := []rune("ab⌘")
    c := chars[rand.Intn(len(chars))]

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
