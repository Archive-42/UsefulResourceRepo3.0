



## Concurrency in Go

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  [Select explained](select-explained.html)
4.  [Data races explained](data-races-explained.html)
5.  [Detect data races](detect-data-races.html)
6.  Deadlock
7.  [Wait for goroutines](wait-for-goroutines-waitgroup.html)
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

# Go: Deadlock

A **deadlock** happens when a group of goroutines are waiting for each other and none of them is able to proceed.

Take a look at this simple example:

    func main() {
            ch := make(chan int)
            ch <- 1
            fmt.Println(<-ch)
    }

The program will get stuck on the channel send operation waiting forever for someone to read the value. Go is able to detect situations like this at runtime. Here is the output from our program:

    fatal error: all goroutines are asleep - deadlock!

    goroutine 1 [chan send]:
    main.main()
            .../deadlock.go:7 +0x6c

## Debugging tips

A goroutine can get stuck

- either because it's waiting for a **channel** or

- because it is waiting for one of the **locks** in the [sync](https://golang.org/pkg/sync/) package.

Typical reasons are:

- No other goroutine has access to the channel or the lock, or

- A group of goroutines are waiting for each other and none of them is able to proceed. (This is the formal defintion of **deadlock**.)

Currently Go only detects when the program as a whole freezes, not when a subset of goroutines get stuck.

With channels it's often easy to figure out what caused a deadlock. Programs that make heavy use of mutexes can on the other hand be notoriously difficult to debug.

<a href="detect-data-races.html" class="prev"></a>

« Prev

Detect data races

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

6 of 12

<a href="wait-for-goroutines-waitgroup.html" class="next"></a>

Next »

Wait for goroutines

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
