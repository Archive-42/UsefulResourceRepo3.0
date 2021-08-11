## Further Reading

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Defer statement](defer.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Write log to file](log-to-file.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to write benchmarks in Go](https://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go)  
<span style="color: grey; font-style: italic; font-size: smaller">by Dave Cheney</span>

[Package testing: Benchmarks](https://golang.org/pkg/testing/#hdr-Benchmarks)  
<span style="color: grey; font-style: italic; font-size: smaller">golang.org</span>

[Proposal: Monotonic Elapsed Time Measurements in Go](https://golang.org/design/12914-monotonic)  
<span style="color: grey; font-style: italic; font-size: smaller">by Russ Cox</span>

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

# Go: Measure execution time

## Measure a piece of code

    start := time.Now()
    …Code to measure elapsed time of…
    duration := time.Since(start)

    // Formatted string, such as "2h3m0.5s" or "4.503μs"
    fmt.Println(duration)

    // Nanoseconds as int64
    fmt.Println(duration.Nanoseconds())

## Measure a function call

You can track the execution time of a complete function call with this one-liner, which logs the result to the standard error stream.

    func foo() {
            defer duration(track("foo"))
            // Code to measure
    }

The helper functions `track` and `duration` are defined as

    func track(msg string) (string, time.Time) {
            return msg, time.Now()
    }

    func duration(msg string, start time.Time) {
            log.Printf("%v: %v\n", msg, time.Since(start))
    }

## Benchmarks

The [`testing`](https://golang.org/pkg/testing/) package has support for benchmarking that can be used to examine the performance of your code.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
