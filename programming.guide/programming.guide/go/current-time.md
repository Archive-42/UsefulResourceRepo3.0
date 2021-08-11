



## Further Reading

[Measure execution time](measure-execution-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days between two dates](days-between-dates.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days in a month](last-day-month-date.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time zones](time-change-convert-location-timezone.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Timer and Ticker explained](time-reset-wait-stop-timeout-cancel-interval.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Current time

Use the [`time.Now`](https://golang.org/pkg/time/#Now) function and the [`time.Unix`](https://golang.org/pkg/time/#Time.Unix) and [`time.UnixNano`](https://golang.org/pkg/time/#Time.UnixNano) methods to get a timestamp.

    now := time.Now()      // current local time
    sec := now.Unix()      // number of seconds since January 1, 1970 UTC
    nsec := now.UnixNano() // number of nanoseconds since January 1, 1970 UTC

    fmt.Println(now)
    fmt.Println(sec)
    fmt.Println(nsec)

    2009-11-10 23:00:00 +0000 UTC m=+0.000000000
    1257894000
    1257894000000000000

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
