



## Further Reading

[Channels explained](channels-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Broadcast a signal on a channel](broadcast-channel.html)  
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

# Go: Close a channel

The [close](https://golang.org/ref/spec#Close) function records that no more values will be sent on a channel. (Sending to or closing a closed channel causes a run-time panic.)

After calling `close`, and after any previously sent values have been received, receive operations will return a zero value without blocking. A multi-valued receive operation additionally returns a boolean indicating whether the value was delivered by a send operation.

    ch := make(chan string)
    go func() {
        ch <- "Hello!"
        close(ch)
    }()
    fmt.Println(<-ch)  // prints "Hello!"
    fmt.Println(<-ch)  // prints the zero value "" without blocking
    fmt.Println(<-ch)  // once again prints ""
    v, ok := <-ch      // v is "", ok is false

## Read until closed

A `for` statement with a `range` clause reads successive values sent on a channel until the channel is closed.

    func main() {
        var ch <-chan Sushi = Producer()
        for s := range ch {
            fmt.Println("Consumed", s)
        }
    }

    func Producer() <-chan Sushi {
        ch := make(chan Sushi)
        go func() {
            ch <- Sushi("海老握り")  // Ebi nigiri
            ch <- Sushi("鮪とろ握り") // Toro nigiri
            close(ch)
        }()
        return ch
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
