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
8.  Broadcast a signal on a channel
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

# Go: Broadcast a signal on a channel

When you **close** a channel, **all readers** receive a zero value.

In this example the `Publish` function returns a channel, which is used to broadcast a signal when a message has been published.

    // Print text after the given time has expired.
    // When done, the wait channel is closed.
    func Publish(text string, delay time.Duration) (wait <-chan struct{}) {
            ch := make(chan struct{})
            go func() {
                    time.Sleep(delay)
                    fmt.Println("BREAKING NEWS:", text)
                    close(ch) // Broadcast to all receivers
            }()
            return ch
    }

Notice that we use a channel of empty structs: `struct{}`. This clearly indicates that the channel will only be used for signalling, not for passing data.

This is how you may use the function.

    func main() {
            wait := Publish("Channels let goroutines communicate.", 5*time.Second)
            fmt.Println("Waiting for the news...")
            <-wait
            fmt.Println("The news is out, time to leave.")
    }

<a href="wait-for-goroutines-waitgroup.html" class="prev"></a>

« Prev

Wait for goroutines

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

8 of 12

<a href="stop-goroutine.html" class="next"></a>

Next »

Stop a goroutine

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
