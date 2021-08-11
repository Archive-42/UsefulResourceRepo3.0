<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Convert byte slice (array) to string](convert-byte-slice-to-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The io.Writer interface](io-writer-interface-explained.html)  
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

Go: Hash checksums
==================

String
------

To compute the checksum of a **string** or **byte slice**, use the `Sum` function from a crypto package such as [`crypto/md5`](https://golang.org/pkg/crypto/md5/), [`crypto/sha1`](https://golang.org/pkg/crypto/sha1/), or [`crypto/sha256`](https://golang.org/pkg/crypto/sha256/):

    s := "Foo"

    md5 := md5.Sum([]byte(s))
    sha1 := sha1.Sum([]byte(s))
    sha256 := sha256.Sum256([]byte(s))

    fmt.Printf("%x\n", md5)
    fmt.Printf("%x\n", sha1)
    fmt.Printf("%x\n", sha256)

    1356c67d7ad1638d816bfb822dd2c25d
    201a6b3053cc1422d2c3670b62616221d2290929
    1cbec737f863e4922cee63cc2ebbfaafcd1cff8b790d8cfd2e6a5d550b648afa

File
----

To compute the checksum of a **file** or other **input stream**:

-   create a new [`hash.Hash`](https://golang.org/pkg/hash/#Hash) from a crypto package such as [`crypto/md5`](https://golang.org/pkg/crypto/md5/), [`crypto/sha1`](https://golang.org/pkg/crypto/sha1/), or [`crypto/sha256`](https://golang.org/pkg/crypto/sha256/),
-   add data by writing to its `io.Writer` function,
-   extract the checksum by calling its `Sum` function.

<!-- -->

    input := strings.NewReader("Foo")

    hash := sha256.New()
    if _, err := io.Copy(hash, input); err != nil {
            log.Fatal(err)
    }
    sum := hash.Sum(nil)

    fmt.Printf("%x\n", sum)

    1cbec737f863e4922cee63cc2ebbfaafcd1cff8b790d8cfd2e6a5d550b648afa

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
