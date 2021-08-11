<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days between two dates](days-between-dates.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days in a month](last-day-month-date.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Package time](https://golang.org/pkg/time/)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

[List of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Time zones

Each [`Time`](https://golang.org/pkg/time/#Time) has an associated [`Location`](https://golang.org/pkg/time/#Location), which is used for display purposes.

The method [`In`](https://golang.org/pkg/time/#Time.In) returns a time with a specific location. Changing the location in this way changes only the presentation; it does not change the instant in time.

Here is a convenience function that changes the location associated with a time.

    // TimeIn returns the time in UTC if the name is "" or "UTC".
    // It returns the local time if the name is "Local".
    // Otherwise, the name is taken to be a location name in
    // the IANA Time Zone database, such as "Africa/Lagos".
    func TimeIn(t time.Time, name string) (time.Time, error) {
            loc, err := time.LoadLocation(name)
            if err == nil {
                    t = t.In(loc)
            }
            return t, err
    }

In use:

    for _, name := range []string{
            "",
            "Local",
            "Asia/Shanghai",
            "America/Metropolis",
    } {
            t, err := TimeIn(time.Now(), name)
            if err == nil {
                    fmt.Println(t.Location(), t.Format("15:04"))
            } else {
                    fmt.Println(name, "<time unknown>")
            }
    }

    UTC 19:32
    Local 20:32
    Asia/Shanghai 03:32
    America/Metropolis <time unknown>

## Timezone Corner Cases

Note the following warning from the docs:

> A daylight savings time transition skips or repeats times. For example, in the United States, March 13, 2011 2:15am never occurred, while November 6, 2011 1:15am occurred twice. In such cases, the choice of time zone, and therefore the time, is not well-defined. Date returns a time that is correct in one of the two zones involved in the transition, but it does not guarantee which. <a href="https://golang.org/pkg/time/#Date" class="quote-source">Package time: Date</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
