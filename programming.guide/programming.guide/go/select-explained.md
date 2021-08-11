<span class="underline"></span>

<span class="underline"></span>

## Concurrency in Go

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  Select explained
4.  [Data races explained](data-races-explained.html)
5.  [Detect data races](detect-data-races.html)
6.  [Deadlock](detect-deadlock.html)
7.  [Wait for goroutines](wait-for-goroutines-waitgroup.html)
8.  [Broadcast a signal on a channel](broadcast-channel.html)
9.  [Stop a goroutine](stop-goroutine.html)
10. [Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)
11. [Mutual exclusion lock (mutex)](mutex-explained.html)
12. [Efficient parallel computation](efficient-parallel-computation.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Select explained

The **select** statement waits for multiple send or receive operations simultaneously.

    // Blocks until there's data available on ch1 or ch2
    select {
    case <-ch1:
            fmt.Println("Received from ch1")
    case <-ch2:
            fmt.Println("Received from ch2")
    }

- The statement blocks as a whole until one of the operations becomes unblocked.
- If several cases can proceed, a single one of them will be chosen at random.

Send and receive operations on a `nil` channel block forever. This can be used to disable a channel in a select statement:

    ch1 = nil // Disables this channel
    select {
    case <-ch1:
            fmt.Println("Received from ch1") // Will not happen
    case <-ch2:
            fmt.Println("Received from ch2")
    }

## Default case

The `default` case is always able to proceed and runs if all other cases are blocked.

    // Never blocks
    select {
    case x := <-ch:
            fmt.Println("Received", x, "from ch")
    default:
            fmt.Println("Nothing available on ch")
    }

## More examples

    // An infinite random binary sequence
    rand := make(chan int)
    for {
            select {
            case rand <- 0: // Note: no statement
            case rand <- 1:
            }
    }

    // A blocking operation with a timeout
    select {
    case news := <-AFP:
            fmt.Println(news)
    case <-time.After(time.Minute):
            fmt.Println("Time out: No news in one minute")
    }

The function [`time.After`](https://golang.org/pkg/time#After) is part of the standard library; it waits for a specified time to elapse and then sends the current time on the returned channel.

    // Block forever
    select {}

A select statement blocks until **at least one** of it's cases can proceed. With zero cases this will never happen.

<a href="channels-explained.html" class="prev"></a>

« Prev

Channels explained

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

3 of 12

<a href="data-races-explained.html" class="next"></a>

Next »

Data races explained

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
