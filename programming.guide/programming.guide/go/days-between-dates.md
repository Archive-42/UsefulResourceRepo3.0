



## Further Reading

[Days in a month](last-day-month-date.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time zones](time-change-convert-location-timezone.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Measure execution time](measure-execution-time.html)  
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

# Go: Days between two dates

    func main() {
            // The leap year 2000 had 366 days.
            t1 := Date(2000, 1, 1)
            t2 := Date(2001, 1, 1)
            days := t2.Sub(t1).Hours() / 24
            fmt.Println(days) // 366
    }

    func Date(year, month, day int) time.Time {
            return time.Date(year, time.Month(month), day, 0, 0, 0, 0, time.UTC)
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
