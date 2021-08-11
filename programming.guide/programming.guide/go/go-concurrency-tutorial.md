<span class="underline"></span>

<span class="underline"></span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  Concurrent programming

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Concurrent programming

This tutorial covers

- concurrent threads of execution (goroutines),
- basic synchronization techniques (channels and locks),
- basic concurrency patterns in Go,
- deadlock and data races,
- waitgroups, timers and tickers,
- parallel computation.

Before you start, you need to know how to write basic Go programs. The resources in [Go: Get started](getting-started-hello-world.html) will help you come up to speed quickly with Go.

<a href="goroutines-explained.html" class="button">Start here</a>

## Table of contents

1.  [Goroutines explained](goroutines-explained.html)
    A goroutine is a lightweight thread of execution.

2.  [Channels explained](channels-explained.html)
    A channel is a mechanism for two goroutines to synchronize execution and communicate by passing values.

3.  [Select explained](select-explained.html)
    A select statement allows you to wait for multiple send or receive operations simultaneously.

4.  [Data races explained](data-races-explained.html)
    A data race is easily introduced by mistake and can lead to situations that are very hard to debug. This article explains how to avoid this headache.

5.  [Detect data races](detect-data-races.html)
    By starting your application with the '-race' option, the Go runtime might be able to detect and inform you about data races.

6.  [Deadlock](detect-deadlock.html)
    The Go runtime can often detect when a program freezes because of a deadlock. This article explains how to debug and solve such issues.

7.  [Wait for goroutines](wait-for-goroutines-waitgroup.html)
    A sync.WaitGroup waits for a group of goroutines to finish.

8.  [Broadcast a signal on a channel](broadcast-channel.html)
    When you close a channel, all readers receive a zero value. This can be used to broadcast a signal to several goroutines on a single channel.

9.  [Stop a goroutine](stop-goroutine.html)
    A goroutine can stop only by returning from it's top level function. To make it stoppable, let it listen to a stop signal on a channel.

10. [Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)
    Timers and Tickers are used to wait for, repeat, and cancel events in the future.

11. [Mutual exclusion lock (mutex)](mutex-explained.html)
    A sync.Mutex is used to synchronize data by explicit locking.

12. [Efficient parallel computation](efficient-parallel-computation.html)
    To efficiently schedule parallel computation on separate CPUs is more of an art than a science. This article gives some rules of thumb.

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
