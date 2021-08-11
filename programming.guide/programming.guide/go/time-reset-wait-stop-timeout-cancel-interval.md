<span class="underline"></span>

<span class="underline"></span>

## Concurrency in Go

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  [Select explained](select-explained.html)
4.  [Data races explained](data-races-explained.html)
5.  [Detect data races](detect-data-races.html)
6.  [Deadlock](detect-deadlock.html)
7.  [Wait for goroutines](wait-for-goroutines-waitgroup.html)
8.  [Broadcast a signal on a channel](broadcast-channel.html)
9.  [Stop a goroutine](stop-goroutine.html)
10. Timer and Ticker explained
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

# Go: Timer and Ticker explained

Timers and Tickers let you execute code in the future, once or repeatedly.

## Timeout (Timer)

[`time.After`](https://golang.org/pkg/time/#After) waits for a specified duration and then sends the current time on the returned channel:

    select {
    case news := <-AFP:
            fmt.Println(news)
    case <-time.After(time.Hour):
            fmt.Println("No news in an hour.")
    }

The underlying [`time.Timer`](https://golang.org/pkg/time/#Timer) will not be recovered by the garbage collector until the timer fires. If this is a concern, use [`time.NewTimer`](https://golang.org/pkg/time/#NewTimer) instead and call its [`Stop`](https://golang.org/pkg/time/#Timer.Stop) method when the timer is no longer needed:

    for alive := true; alive; {
            timer := time.NewTimer(time.Hour)
            select {
            case news := <-AFP:
                    timer.Stop()
                    fmt.Println(news)
            case <-timer.C:
                    alive = false
                    fmt.Println("No news in an hour. Service aborting.")
            }
    }

## Repeat (Ticker)

[`time.Tick`](https://golang.org/pkg/time/#Tick) returns a channel that delivers clock ticks at even intervals:

    go func() {
            for now := range time.Tick(time.Minute) {
                    fmt.Println(now, statusUpdate())
            }
    }()

The underlying [`time.Ticker`](https://golang.org/pkg/time/#Ticker) will not be recovered by the garbage collector. If this is a concern, use [`time.NewTicker`](https://golang.org/pkg/time/#NewTicker) instead and call its [`Stop`](https://golang.org/pkg/time/#Timer.Stop) method when the ticker is no longer needed.

## Wait, act and cancel

[`time.AfterFunc`](https://golang.org/pkg/time/#AfterFunc) waits for a specified duration and then calls a function in its own goroutine. It returns a [`time.Timer`](https://golang.org/pkg/time/#Timer) that can be used to cancel the call:

    func Foo() {
            timer = time.AfterFunc(time.Minute, func() {
                    log.Println("Foo run for more than a minute.")
            })
            defer timer.Stop()

            // Do heavy work
    }

<a href="stop-goroutine.html" class="prev"></a>

« Prev

Stop a goroutine

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

10 of 12

<a href="mutex-explained.html" class="next"></a>

Next »

Mutual exclusion lock (mutex)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
