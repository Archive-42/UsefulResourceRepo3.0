## Further Reading

[Use a sync.Mutex or a channel?](https://github.com/golang/go/wiki/MutexOrChannel)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Wiki</span>

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
10. [Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)
11. Mutual exclusion lock (mutex)
12. [Efficient parallel computation](efficient-parallel-computation.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Mutual exclusion lock (mutex)

Mutexes let you synchronize data access by explicit locking, without channels.

**Example:** Here's a basic example illustrating `Lock` and `Unlock`:

    mutex := sync.Mutex{}
    mutex.Lock()
    go func() {
            mutex.Lock() // Wait for main to call Unlock
            fmt.Println("In goroutine")
            mutex.Unlock()
    }()
    time.Sleep(time.Second)
    fmt.Println("In main")
    mutex.Unlock()
    time.Sleep(time.Second)

`"In main"` will be printed before `"In goroutine"`, despite the fact that the main routine sleeps for a second before the call to `Println`.

## Use with caution!

For this type of locking to be safe, it's crucial that all accesses to the shared data, both reads and writes, are performed only when a goroutine holds the lock. One mistake by a single goroutine is enough to introduce a data race and break the program.

Because of this you should consider designing a custom data structure with a clean API and make sure that all the synchronization is done internally. Here's a more interesting example:

**Example:** In this example we build a safe and easy-to-use concurrent data structure, `AtomicInt`, that stores a single integer. Any number of goroutines can safely access this number through the `Add` and `Value` methods.

    // AtomicInt is a concurrent data structure that holds an int.
    // Its zero value is 0.
    type AtomicInt struct {
        mu sync.Mutex // A lock than can be held by one goroutine at a time.
        n  int
    }

    // Add adds n to the AtomicInt as a single atomic operation.
    func (a *AtomicInt) Add(n int) {
        a.mu.Lock() // Wait for the lock to be free and then take it.
        a.n += n
        a.mu.Unlock() // Release the lock.
    }

    // Value returns the value of a.
    func (a *AtomicInt) Value() int {
        a.mu.Lock()
        n := a.n
        a.mu.Unlock()
        return n
    }

    func main() {
        wait := make(chan struct{})
        var n AtomicInt
        go func() {
            n.Add(1) // one access
            close(wait)
        }()
        n.Add(1) // another concurrent access
        <-wait
        fmt.Println(n.Value()) // Output: 2
    }

<a href="time-reset-wait-stop-timeout-cancel-interval.html" class="prev"></a>

« Prev

Timer and Ticker explained

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

11 of 12

<a href="efficient-parallel-computation.html" class="next"></a>

Next »

Efficient parallel computation

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
