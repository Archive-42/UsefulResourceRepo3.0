<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Disable logging](disable-logging-output.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Defer statement](defer.html)  
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

Go: Write log to file
=====================

This code appends a log message to the file `text.log`. It creates the file if it doesn't already exist.

    f, err := os.OpenFile("text.log", os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)
    if err != nil {
            log.Println(err)
    }
    defer f.Close()

    logger := log.New(f, "prefix", log.LstdFlags)
    logger.Println("text to append")
    logger.Println("more text to append")

Contents of `text.log`:

    prefix: 2017/10/20 07:52:58 text to append
    prefix: 2017/10/20 07:52:58 more text to append

-   [`log.New`](https://golang.org/pkg/log/#New) creates a new [`log.Logger`](https://golang.org/pkg/log/#Logger) that writes to `f`.
-   The prefix appears at the beginning of each generated log line.
-   The [`flag`](https://golang.org/pkg/log/#pkg-constants) argument defines which text to prefix to each log entry.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
