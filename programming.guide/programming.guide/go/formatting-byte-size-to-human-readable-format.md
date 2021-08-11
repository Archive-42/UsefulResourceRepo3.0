<span class="underline"></span>

<span class="underline"></span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Format byte size to human readable format
=============================================

Here’s how to convert `1000` to `"1 kB"`, `1000000` to `"1 MB"` etc.

    func ByteCountDecimal(b int64) string {
            const unit = 1000
            if b < unit {
                    return fmt.Sprintf("%d B", b)
            }
            div, exp := int64(unit), 0
            for n := b / unit; n >= unit; n /= unit {
                    div *= unit
                    exp++
            }
            return fmt.Sprintf("%.1f %cB", float64(b)/float64(div), "kMGTPE"[exp])
    }

    func ByteCountBinary(b int64) string {
            const unit = 1024
            if b < unit {
                    return fmt.Sprintf("%d B", b)
            }
            div, exp := int64(unit), 0
            for n := b / unit; n >= unit; n /= unit {
                    div *= unit
                    exp++
            }
            return fmt.Sprintf("%.1f %ciB", float64(b)/float64(div), "KMGTPE"[exp])
    }

Example input/output:

               Input     Decimal (SI)     Binary (IEC)
                   0            "0 B"            "0 B"
                  27           "27 B"           "27 B"
                 999          "999 B"          "999 B"
                1000         "1.0 kB"         "1000 B"
                1023         "1.0 kB"         "1023 B"
                1024         "1.0 kB"        "1.0 KiB"
                1728         "1.7 kB"        "1.7 KiB"
       1855425871872         "1.9 TB"        "1.7 TiB"
       math.MaxInt64         "9.2 EB"        "8.0 EiB

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
