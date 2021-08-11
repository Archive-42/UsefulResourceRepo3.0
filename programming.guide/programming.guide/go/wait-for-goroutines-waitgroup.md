



## Concurrency in Go

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  [Select explained](select-explained.html)
4.  [Data races explained](data-races-explained.html)
5.  [Detect data races](detect-data-races.html)
6.  [Deadlock](detect-deadlock.html)
7.  Wait for goroutines
8.  [Broadcast a signal on a channel](broadcast-channel.html)
9.  [Stop a goroutine](stop-goroutine.html)
10. [Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)
11. [Mutual exclusion lock (mutex)](mutex-explained.html)
12. [Efficient parallel computation](efficient-parallel-computation.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Wait for goroutines

A [sync.WaitGroup](https://golang.org/pkg/sync/) waits for a group of goroutines to finish.

    var wg sync.WaitGroup
    wg.Add(2)

    go func() {
            // Do work
            wg.Done()
    }()

    go func() {
            // Do work
            wg.Done()
    }()

    wg.Wait()

- First the main goroutine calls [`Add`](https://golang.org/pkg/sync/#WaitGroup.Add) to set the number of goroutines to wait for.
- Then two new goroutines run and call [`Done`](https://golang.org/pkg/sync/#WaitGroup.Done) when finished.

_At the same time_, [`Wait`](https://golang.org/pkg/sync/#WaitGroup.Wait) is used to block until these two goroutines have finished.

**Note:** A WaitGroup must not be copied after first use.

<a href="detect-deadlock.html" class="prev"></a>

« Prev

Deadlock

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

7 of 12

<a href="broadcast-channel.html" class="next"></a>

Next »

Broadcast a signal on a channel

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
