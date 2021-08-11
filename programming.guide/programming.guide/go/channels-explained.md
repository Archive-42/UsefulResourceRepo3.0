<span class="underline"></span>

<span class="underline"></span>

Concurrency in Go
-----------------

1.  [Goroutines explained](goroutines-explained.html)
2.  Channels explained
3.  [Select explained](select-explained.html)
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

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Channels explained
======================

A **channel** is a mechanism for goroutines to **synchronize** execution and **communicate** by passing values.

The `<-` operator specifies the channel direction, **send** or **receive**. If no direction is given, the channel is **bi-directional**.

    // can only be used to send float64s
    chan<- float64

    // can only be used to receive ints
    <-chan int

    // can be used to send and receive values of type Sushi
    chan Sushi

A new channel value can be made using the built-in function `make`:

    // unbuffered channel of ints
    ic := make(chan int)

    // buffered channel with room for 10 elements
    wc := make(chan *Work, 10)

**To send** a value on a channel, use `<-` as a binary operator.

**To receive** a value on a channel, use it as a unary operator.

    ic <- 3      // Send 3 on the channel.
    work := <-wc // Receive a pointer to Work from the channel.

Buffered and unbuffered channels
--------------------------------

-   If the capacity of a channel is zero or absent, the channel is **unbuffered** and the sender blocks until the receiver has received the value.

-   If the channel **has a buffer**, the sender blocks only until the value has been copied to the buffer; if the buffer is full, this means waiting until some receiver has retrieved a value.

-   Receivers always block until there is data to receive.

-   Sending or receiving from a `nil` channel blocks forever.

Closing a channel
-----------------

The `close` function records that no more values will be sent on a channel. (Sending to or closing a closed channel causes a run-time panic. Closing a `nil` channel also causes a run-time panic.)

After calling `close`, and after any previously sent values have been received, receive operations will return a [zero value](default-zero-value.html) without blocking. A multi-valued receive operation additionally returns an indication of whether the channel is closed.

    ch := make(chan string)
    go func() {
            ch <- "Hello!"
            close(ch)
    }()

    fmt.Println(<-ch) // Print "Hello!".
    fmt.Println(<-ch) // Print the zero value "" without blocking.
    fmt.Println(<-ch) // Once again print "".
    v, ok := <-ch     // v is "", ok is false.

    // Receive values from ch until closed.
    for v := range ch {
            fmt.Println(v) // Will not be executed.
    }

Note that it is only necessary to close a channel if a receiver is looking for a close.

Example
-------

In the following example we let the `Publish` function return a channel, which is used to broadcast a message when the text has been published.

    // Publish prints text to stdout after the given time has expired.
    // It closes the wait channel when the text has been published.
    func Publish(text string, delay time.Duration) (wait <-chan struct{}) {
            ch := make(chan struct{})
            go func() {
                    time.Sleep(delay)
                    fmt.Println(text)
                    close(ch)
            }()
            return ch
    }

Notice that we use a channel of empty structs to indicate that the channel will only be used for signalling, not for passing data.

This is how you might use this function.

    wait := Publish("important news", 2 * time.Minute)
    // Do some more work.
    <-wait // Block until the text has been published.

Deadlock
--------

If you remove the call to `close` from the example above, the goroutine started by the `Publish` function will print the news and leave the code in the other goroutine waiting forever. This condition is known as a deadlock.

A **deadlock** is a situation in which goroutines are waiting for each other and none of them is able to proceed.

Go has a mechanism for [detecting deadlocks](detect-deadlock.html).

<a href="goroutines-explained.html" class="prev"></a>

« Prev

Goroutines explained

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

2 of 12

<a href="select-explained.html" class="next"></a>

Next »

Select explained

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
