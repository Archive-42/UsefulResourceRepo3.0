## Further Reading

[What is a rune?](rune.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Strings, bytes, runes and characters in Go](https://blog.golang.org/strings)  
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

# Go: Reverse a UTF-8 encoded string

This function returns a string with the UTF-8 encoded characters of `s` in reverse order. Invalid UTF-8 sequences, if any, will be reversed byte by byte.

    func ReverseUTF8(s string) string {
            res := make([]byte, len(s))
            prevPos, resPos := 0, len(s)
            for pos := range s {
                    resPos -= pos - prevPos
                    copy(res[resPos:], s[prevPos:pos])
                    prevPos = pos
            }
            copy(res[0:], s[prevPos:])
            return string(res)
    }

Example usage:

    for _, s := range []string{
            "Ångström",
            "Hello, 世界",
            "\xff\xfe\xfd", // invalid UTF-8
    } {
            fmt.Printf("%q\n", ReverseUTF8(s))
    }

    "mörtsgnÅ"
    "界世 ,olleH"
    "\xfd\xfe\xff"

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
