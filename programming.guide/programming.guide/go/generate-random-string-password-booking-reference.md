<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Cryptographically secure random numbers](crypto-rand-int.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Generate a random UUID (GUID)](generate-uuid-guid.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

Go: Generate a random string (password, booking reference)
==========================================================

Random Unicode string
---------------------

    rand.Seed(time.Now().UnixNano())
    chars := []rune("ABCDEFGHIJKLMNOPQRSTUVWXYZÅÄÖ" +
            "abcdefghijklmnopqrstuvwxyzåäö" +
            "0123456789")
    length := 8
    buf := make([]rune, length)
    for i := range buf {
            buf[i] = chars[rand.Intn(len(chars))]
    }
    str := string(buf)

Random ASCII string with at least 1 digit and 1 special character
-----------------------------------------------------------------

If all characters can be represented by a single byte, e.g. ASCII characters, you can use `[]byte` instead of `[]rune`.

    rand.Seed(time.Now().UnixNano())
    digits := "0123456789"
    specials := "~=+%^*/()[]{}/!@#$?|"
    all := "ABCDEFGHIJKLMNOPQRSTUVWXYZ" +
            "abcdefghijklmnopqrstuvwxyz" +
            digits + specials
    length := 8
    buf := make([]byte, length)
    buf[0] = digits[rand.Intn(len(digits))]
    buf[1] = specials[rand.Intn(len(specials))]
    for i := 2; i < length; i++ {
            buf[i] = all[rand.Intn(len(all))]
    }
    for i := len(buf) - 1; i > 0; i-- {
            j := rand.Intn(i + 1)
            buf[i], buf[j] = buf[j], buf[i]
    }
    str := string(buf)

**Warning:** If you're building a password generator, consider using a string generation algorithm from a high-quality cryptographic library. If you're running your own, and you probably shouldn't, package [`crypto/rand`](https://golang.org/pkg/crypto/rand/) offers a cryptographically secure pseudorandom number generator.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
