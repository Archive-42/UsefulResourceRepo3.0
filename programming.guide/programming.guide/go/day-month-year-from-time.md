



## Further Reading

[Day of week](day-of-week-int.html)  
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

# Go: Get year, month, day from time

The [`Date`](https://golang.org/pkg/time/#Time.Date) function returns the year, month and day of a [`time.Time`](https://golang.org/pkg/time/#Time).

    func (t Time) Date() (year int, month Month, day int)

In use:

    year, month, day := time.Now().Date()
    fmt.Println(year, month, day)      // For example 2009 November 10
    fmt.Println(year, int(month), day) // For example 2009 11 10

You can also extract the information with seperate calls:

    t := time.Now()
    year := t.Year()   // type int
    month := t.Month() // type time.Month
    day := t.Day()     // type int

The [`time.Month`](https://golang.org/pkg/time/#Month) type specifies a month of the year (January = 1, …).

    type Month int

    const (
            January Month = 1 + iota
            February
            March
            April
            May
            June
            July
            August
            September
            October
            November
            December
    )

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
