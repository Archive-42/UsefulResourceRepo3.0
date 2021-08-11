



## Further Reading

[Get year, month, day from time](day-month-year-from-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time zones](time-change-convert-location-timezone.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days between two dates](days-between-dates.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days in a month](last-day-month-date.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[iota](iota.html)  
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

# Go: Day of week

The [`Weekday`](https://golang.org/pkg/time/#Time.Weekday) function returns returns the day of the week of a [`time.Time`](https://golang.org/pkg/time/#Time).

    func (t Time) Weekday() Weekday

In use:

    weekday := time.Now().Weekday()
    fmt.Println(weekday)      // "Tuesday"
    fmt.Println(int(weekday)) // "2"

## Type Weekday

The [`time.Weekday`](https://golang.org/pkg/time/#Weekday) type specifies a day of the week (Sunday = 0, …).

    type Weekday int

    const (
            Sunday Weekday = iota
            Monday
            Tuesday
            Wednesday
            Thursday
            Friday
            Saturday
    )

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
