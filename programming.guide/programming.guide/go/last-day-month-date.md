## Further Reading

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time zones](time-change-convert-location-timezone.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days between two dates](days-between-dates.html)  
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

# Go: Days in a month

To compute the last day of a month, you can use the fact that [`time.Date`](https://golang.org/pkg/time/#Date) accepts values outside their usual ranges; the values are normalized during the conversion. For example, March 0 converts to the last day of February:

    func main() {
            t := Date(2000, 3, 0) // the day before 2000-03-01
            fmt.Println(t)        // 2000-02-29 00:00:00 +0000 UTC
    }

    func Date(year, month, day int) time.Time {
            return time.Date(year, time.Month(month), day, 0, 0, 0, 0, time.UTC)
    }

[`AddDate`](https://golang.org/pkg/time/#Time.AddDate) normalizes its result in the same way. For example, adding one month to October 31 yields December 1, the normalized form of November 31:

    t = Date(2000, 10, 31).AddDate(0, 1, 0) // a month after October 31
    fmt.Println(t)                          // 2000-12-01 00:00:00 +0000 UTC

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
