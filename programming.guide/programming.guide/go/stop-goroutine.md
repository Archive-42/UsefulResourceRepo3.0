<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Go Concurrency Patterns: Context](https://blog.golang.org/context)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Go Concurrency Patterns: Pipelines and cancellation](https://blog.golang.org/pipelines)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

Concurrency in Go
-----------------

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  [Select explained](select-explained.html)
4.  [Data races explained](data-races-explained.html)
5.  [Detect data races](detect-data-races.html)
6.  [Deadlock](detect-deadlock.html)
7.  [Wait for goroutines](wait-for-goroutines-waitgroup.html)
8.  [Broadcast a signal on a channel](broadcast-channel.html)
9.  Stop a goroutine
10. [Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)
11. [Mutual exclusion lock (mutex)](mutex-explained.html)
12. [Efficient parallel computation](efficient-parallel-computation.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Stop a goroutine
====================

One goroutine can't forcibly stop another—a gorou­tine can stop only by returning from it's top level function.

To make a goroutine stoppable, let it listen for a stop signal on a channel. Here's an example:

    quit := make(chan struct{})
    go func() {
            for {
                    select {
                    case <-quit:
                            return
                    default:
                            // …
                    }
            }
    }()

    // …
    close(quit)

Sometimes it's convenient to use a single channel for both data and signalling:

    // Generator returns a channel that produces the numbers 1, 2, 3,…
    // To stop the underlying goroutine, close the channel.
    func Generator() chan int {
            ch := make(chan int)
            go func() {
                    n := 1
                    for {
                            select {
                            case ch <- n:
                                    n++
                            case <-ch:
                                    return
                            }
                    }
            }()
            return ch
    }

    func main() {
            number := Generator()
            fmt.Println(<-number)
            fmt.Println(<-number)
            close(number)
            // …
    }

    1
    2

<a href="broadcast-channel.html" class="prev"></a>

« Prev

Broadcast a signal on a channel

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

9 of 12

<a href="time-reset-wait-stop-timeout-cancel-interval.html" class="next"></a>

Next »

Timer and Ticker explained

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
