<span class="underline"></span>

<span class="underline"></span>

Concurrency in Go
-----------------

1.  Goroutines explained
2.  [Channels explained](channels-explained.html)
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

Goroutines explained
====================

The **go** statement runs a function in a separate thread of execution: a **goroutine**.

    go list.Sort() // Run list.Sort in parallel; don’t wait for it.

All goroutines in a single program share the same address space.

The following program will print "Hello from main goroutine". It *might* also print "Hello from another goroutine", depending on which of the two goroutines finish first.

    func main() {
            go fmt.Println("Hello from another goroutine")
            fmt.Println("Hello from main goroutine")

            // At this point the program execution stops and all
            // active goroutines are killed.
    }

The next program will, most likely, print both "Hello from main goroutine" and "Hello from another goroutine". They may be printed in any order. Yet another possibility is that the second goroutine is extremely slow and doesn’t print its message before the program ends.

    func main() {
            go fmt.Println("Hello from another goroutine")
            fmt.Println("Hello from main goroutine")

            time.Sleep(time.Second) // wait for other goroutine to finish
    }

Here is a somewhat more realistic example, where we define a function that uses concurrency to postpone an event.

    // Publish prints text to stdout after the given time has expired.
    // It doesn’t block but returns right away.
    func Publish(text string, delay time.Duration) {
            go func() {
                    time.Sleep(delay)
                    fmt.Println("BREAKING NEWS:", text)
            }() // Note the parentheses. We must call the anonymous function.
    }

This is how you might use the `Publish` function.

    func main() {
            Publish("A goroutine starts a new thread of execution.", 5*time.Second)
            fmt.Println("Let’s hope the news will published before I leave.")

            // Wait for the news to be published.
            time.Sleep(10 * time.Second)

            fmt.Println("Ten seconds later: I’m leaving now.")
    }

The program will, most likely, print the following three lines, in the given order and with a five second break in between each line.

    $ go run publish1.go
    Let’s hope the news will published before I leave.
    BREAKING NEWS: A goroutine starts a new thread of execution.
    Ten seconds later: I’m leaving now.

In general it’s not possible to arrange for threads to wait for each other by sleeping. Go’s main method for synchronization is to use [channels](channels-explained.html).

Implementation
--------------

Goroutines are lightweight, costing little more than the allocation of stack space. The stacks start small and grow by allocating and freeing heap storage as required. Internally goroutines act like coroutines that are multiplexed among multiple operating system threads.

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

1 of 12

<a href="channels-explained.html" class="next"></a>

Next »

Channels explained

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
