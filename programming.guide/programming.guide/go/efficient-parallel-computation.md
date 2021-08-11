



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
11. [Mutual exclusion lock (mutex)](mutex-explained.html)
12. Efficient parallel computation



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Efficient parallel computation

Dividing a large compu­tation into work units for parallel pro­cessing is more of an art than a science. Here are some rules of thumb.

- Each work unit should take about 100μs to 1ms to compute.
- If the units are too small, the adminis­trative over­head of divi­ding the problem and sched­uling sub-problems might be too large.
- If the units are too big, the whole computation may have to wait for a single slow work item to finish. This slowdown can happen for many reasons, such as scheduling, interrupts from other processes, and unfortunate memory layout. (Note that the number of work units is independent of the number of CPUs.)
- Try to minimize the amount of data sharing. Concurrent writes can be very costly, particularly so if goroutines execute on separate CPUs. Sharing data for reading is often much less of a problem.
- Strive for good locality when accessing data. If data can be kept in cache memory, data loading and storing will be dramatically faster. Once again, this is particularly important for writing.

## Example

The following example shows how to divide a costly computation and distribute it on all available CPUs. This is the code we want to optimize.

    type Vector []float64

    // Convolve computes w = u * v, where w[k] = Σ u[i]*v[j], i + j = k.
    // Precondition: len(u) > 0, len(v) > 0.
    func Convolve(u, v Vector) Vector {
        n := len(u) + len(v) - 1
        w := make(Vector, n)
        for k := 0; k < n; k++ {
            w[k] = mul(u, v, k)
        }
        return w
    }

    // mul returns Σ u[i]*v[j], i + j = k.
    func mul(u, v Vector, k int) float64 {
        var res float64
        n := min(k+1, len(u))
        j := min(k, len(v)-1)
        for i := k - j; i < n; i, j = i+1, j-1 {
            res += u[i] * v[j]
        }
        return res
    }

The idea is simple: identify work units of suitable size and then run each work unit in a separate goroutine. Here is a parallel version of `Convolve`.

    func Convolve(u, v Vector) Vector {
        n := len(u) + len(v) - 1
        w := make(Vector, n)

        // Divide w into work units that take ~100μs-1ms to compute.
        size := max(1, 1000000/n)

        var wg sync.WaitGroup
        for i, j := 0, size; i < n; i, j = j, j+size {
            if j > n {
                j = n
            }
            // The goroutines share memory, but only for reading.
            wg.Add(1)
            go func(i, j int) {
                for k := i; k < j; k++ {
                    w[k] = mul(u, v, k)
                }
                wg.Done()
            }(i, j)
        }
        wg.Wait()
        return w
    }

## Limiting the number of goroutines

When the work units have been defined, it’s often best to leave the scheduling to the runtime and the operating system. However, if needed, you can tell the runtime how many goroutines you want executing code simultaneously:

    func init() {
        numcpu := runtime.NumCPU()
        runtime.GOMAXPROCS(numcpu) // Try to use all available CPUs.
    }

<a href="mutex-explained.html" class="prev"></a>

« Prev

Mutual exclusion lock (mutex)

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

12 of 12

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
