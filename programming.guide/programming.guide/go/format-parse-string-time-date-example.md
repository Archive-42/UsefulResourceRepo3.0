<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Current time](current-time.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time zones](time-change-convert-location-timezone.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days between two dates](days-between-dates.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Days in a month](last-day-month-date.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Go: Format a time or date

To format a date use the [`Format`](https://golang.org/pkg/time/#Time.Format) method:

    func (t Time) Format(layout string) string

To parse a date string use the [`time.Parse`](https://golang.org/pkg/time/#Parse) function:

    func Parse(layout, value string) (Time, error)

The `layout` parameter describes the format of a time value. It should be the _magical reference date_

    Mon Jan 2 15:04:05 MST 2006

formatted the same way as the value is expected to be formatted.

**Example:** To parse `"2017-08-31"` we use the layout string `"2006-01-02"` since that is the yyyy-mm-dd formatting of the magical reference date.

    input := "2017-08-31"
    layout := "2006-01-02"
    t, _ := time.Parse(layout, input)
    fmt.Println(t)                       // 2017-08-31 00:00:00 +0000 UTC
    fmt.Println(t.Format("02-Jan-2006")) // 31-Aug-2017

What's magical about Mon Jan 2 15:04:05 MST 2006? By formatting this date a bit differently…

    01/02 03:04:05PM '06 -0700

…we see that no two fields are the same. This means that for this particular date, each field can be identified unambigously regardless of the formatting.

## Common layouts

<table><thead><tr class="header"><th>Go layout</th><th>Java notation</th><th>C notation</th><th>Notes</th></tr></thead><tbody><tr class="odd"><td>2006-01-02</td><td>yyyy-MM-dd</td><td>%F</td><td>ISO 8601</td></tr><tr class="even"><td>20060102</td><td>yyyyMMdd</td><td>%Y%m%d</td><td>ISO 8601</td></tr><tr class="odd"><td>January 02, 2006</td><td>MMMM dd, yyyy</td><td>%B %d, %Y</td><td></td></tr><tr class="even"><td>02 January 2006</td><td>dd MMMM yyyy</td><td>%d %B %Y</td><td></td></tr><tr class="odd"><td>02-Jan-2006</td><td>dd-MMM-yyyy</td><td>%d-%b-%Y</td><td></td></tr><tr class="even"><td>01/02/06</td><td>MM/dd/yy</td><td>%D</td><td>US</td></tr><tr class="odd"><td>01/02/2006</td><td>MM/dd/yyyy</td><td>%m/%d/%Y</td><td>US</td></tr><tr class="even"><td>010206</td><td>MMddyy</td><td>%m%d%y</td><td>US</td></tr><tr class="odd"><td>Jan-02-06</td><td>MMM-dd-yy</td><td>%b-%d-%y</td><td>US</td></tr><tr class="even"><td>Jan-02-2006</td><td>MMM-dd-yyyy</td><td>%b-%d-%Y</td><td>US</td></tr><tr class="odd"><td>06</td><td>yy</td><td>%y</td><td></td></tr><tr class="even"><td>Mon</td><td>EEE</td><td>%a</td><td></td></tr><tr class="odd"><td>Monday</td><td>EEEE</td><td>%A</td><td></td></tr><tr class="even"><td>Jan-06</td><td>MMM-yy</td><td>%b-%y</td><td></td></tr></tbody></table>

## Time

<table><thead><tr class="header"><th>Go layout</th><th>Java notation</th><th>C notation</th><th>Notes</th></tr></thead><tbody><tr class="odd"><td>15:04</td><td>HH:mm</td><td>%R</td><td></td></tr><tr class="even"><td>15:04:05</td><td>HH:mm:ss</td><td>%T</td><td>ISO 8601</td></tr><tr class="odd"><td>3:04 PM</td><td>K:mm a</td><td>%l:%M %p</td><td>US</td></tr><tr class="even"><td>03:04:05 PM</td><td>KK:mm:ss a</td><td>%r</td><td>US</td></tr></tbody></table>

## Date and time

<table><thead><tr class="header"><th>Go layout</th><th>Java notation</th><th>C notation</th><th>Notes</th></tr></thead><tbody><tr class="odd"><td>2006-01-02T15:04:05</td><td>yyyy-MM-dd'T'HH:mm:ss</td><td>%FT%T</td><td>ISO 8601</td></tr><tr class="even"><td>2006-01-02T15:04:05-0700</td><td>yyyy-MM-dd'T'HH:mm:ssZ</td><td>%FT%T%z</td><td>ISO 8601</td></tr><tr class="odd"><td>2 Jan 2006 15:04:05</td><td>d MMM yyyy HH:mm:ss</td><td>%e %b %Y %T</td><td></td></tr><tr class="even"><td>2 Jan 2006 15:04</td><td>d MMM yyyy HH:mm</td><td>%e %b %Y %R</td><td></td></tr><tr class="odd"><td>Mon, 2 Jan 2006 15:04:05 MST</td><td>EEE, d MMM yyyy HH:mm:ss z</td><td>%a, %e %b %Y %T %Z</td><td>RFC 1123<br />
RFC 822</td></tr></tbody></table>

## Corner cases

Here are some corner cases not handled by the time package.

- It's not possible to specify that an hour should be rendered without a leading zero in a 24-hour time format.

- It's not possible to specify midnight as `24:00` instead of `00:00`. A typical usage for this would be giving opening hours ending at midnight, such as `07:00-24:00`.

- It's not possible to specify a time containing a leap second: `23:59:60`. In fact, the library assumes a Gregorian calendar with no leap seconds.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
