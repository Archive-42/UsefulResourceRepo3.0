<span class="underline"></span>

<span class="underline"></span>

Related
-------

[The io.Writer interface](io-writer-interface-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go Walkthrough: io package](https://medium.com/go-walkthrough/go-walkthrough-io-package-8ac5e95a9fbd)  
<span style="color: grey; font-style: italic; font-size: smaller">by Ben Johnson</span>

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

Go: The io.Reader interface
===========================

The [`io.Reader`](https://golang.org/pkg/io/#Reader) interface represents an entity from which you can read a stream of bytes:

    type Reader interface {
            Read(buf []byte) (n int, err error)
    }

`Read` reads up to `len(buf)` bytes into `buf` and returns the number of bytes read; it returns an [`io.EOF`](https://golang.org/pkg/io/#pkg-variables) error when the stream ends.

Example
-------

The standard library provides numerous Reader [implementations](https://golang.org/search?q=Read#Global) (including in-memory byte buffers, files and network connections), and Readers are accepted as input by many utilities (including the HTTP client and server implementations).

As an example, you can create a Reader from a string using the [`strings.Reader`](https://golang.org/pkg/strings/#Reader) function and then pass the Reader directly to the [`http.Post`](https://golang.org/pkg/net/http/#Post) function in package [`net/http`](https://golang.org/pkg/net/http/). The Reader is then used as the source for the data to be posted:

    r := strings.NewReader("my request")
    resp, err := http.Post("http://foo.bar", "application/x-www-form-urlencoded", r)

Since `http.Post` uses a Reader instead of a `[]byte` it's trivial to, for instance, use the contents of a file.

Reading directly from a byte stream
-----------------------------------

You can use the `Read` function directly (this is the least common use case):

    r := strings.NewReader("abcde")

    buf := make([]byte, 4)
    for {
            n, err := r.Read(buf)
            fmt.Println(n, err, buf[:n])
            if err == io.EOF {
                    break
            }
    }
    // Output:
    // 4 <nil> [97 98 99 100]
    // 1 <nil> [101]
    // 0 EOF []

Use [`io.ReadFull`](https://golang.org/pkg/io/#ReadFull) to read exactly `len(buf)` bytes into `buf`:

    r := strings.NewReader("abcde")

    buf := make([]byte, 4)
    if _, err := io.ReadFull(r, buf); err != nil {
            log.Fatal(err)
    }
    fmt.Println(buf)

    if _, err := io.ReadFull(r, buf); err != nil {
            fmt.Println(err)
    }
    // Output:
    // [97 98 99 100]
    // unexpected EOF

Use [`ioutil.ReadAll`](https://golang.org/pkg/io/ioutil/#ReadAll) to read everything:

    r := strings.NewReader("abcde")

    buf, err := ioutil.ReadAll(r)
    if err != nil {
            log.Fatal(err)
    }
    fmt.Println(buf)
    // Output: [97 98 99 100 101]

Buffered reading and scanning
-----------------------------

The [`bufio.Reader`](https://golang.org/pkg/bufio/#Reader) and [`bufio.Scanner`](https://golang.org/pkg/bufio/#Scanner) types wrap a Reader creating another Reader that also implements the interface but provides buffering and some help for textual input.

In this example we use a [`bufio.Scanner`](https://golang.org/pkg/bufio/#Scanner) to count the number of words in a text:

    const input = `Beware of bugs in the above code;
    I have only proved it correct, not tried it.`

    scanner := bufio.NewScanner(strings.NewReader(input))
    scanner.Split(bufio.ScanWords) // Set the split function.

    count := 0
    for scanner.Scan() {
            count++
    }
    if err := scanner.Err(); err != nil {
            fmt.Println(err)
    }
    fmt.Println(count)
    // Output: 16

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
