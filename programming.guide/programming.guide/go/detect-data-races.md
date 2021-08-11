<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Data Race Detector](https://golang.org/doc/articles/race_detector.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

Concurrency in Go
-----------------

1.  [Goroutines explained](goroutines-explained.html)
2.  [Channels explained](channels-explained.html)
3.  [Select explained](select-explained.html)
4.  [Data races explained](data-races-explained.html)
5.  Detect data races
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

Go: Detect data races
=====================

Data races can happen easily and are hard to debug. Luckily, the Go runtime is often able to help.

Use `-race` to enable the built-in data race detector.

    $ go test -race somepkg
    $ go run -race somepkg

Example
-------

Here's a program with a data race:

    package main
    import "fmt"

    func main() {
            i := 0
            go func() {
                    i++ // write
            }()
            fmt.Println(i) // concurrent read
    }

Running this program with the `-race` options tells us that there's a race between the write at line 7 and the read at line 9:

    $ go run -race main.go
    0
    ==================
    WARNING: DATA RACE
    Write by goroutine 6:
      main.main.func1()
          /tmp/main.go:7 +0x44

    Previous read by main goroutine:
      main.main()
          /tmp/main.go:9 +0x7e

    Goroutine 6 (running) created at:
      main.main()
          /tmp/main.go:8 +0x70
    ==================
    Found 1 data race(s)
    exit status 66

Details
-------

The data race detector does not perform any static analysis. It checks the memory access in runtime and only for the code paths that are actually executed.

It runs on darwin/amd64, freebsd/amd64, linux/amd64 and windows/amd64.

The overhead varies, but typically there's a 5-10x increase in memory usage, and 2-20x increase in execution time.

<a href="data-races-explained.html" class="prev"></a>

« Prev

Data races explained

[](go-concurrency-tutorial.html#toc)

TOC

Concurrency in Go

5 of 12

<a href="detect-deadlock.html" class="next"></a>

Next »

Deadlock

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
