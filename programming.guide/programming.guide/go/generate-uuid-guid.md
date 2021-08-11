



## Further Reading

[UUID package for Go language](https://github.com/satori/go.uuid)  
<span style="color: grey; font-style: italic; font-size: smaller">by Maxim Bublis</span>

[Generate a random string (password, booking reference)](generate-random-string-password-booking-reference.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Cryptographically secure random numbers](crypto-rand-int.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Cryptographically secure pseudorandom number generator](https://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

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

# Go: Generate a random UUID (GUID)

Use the [`rand.Read`](https://golang.org/pkg/crypto/rand/#Read) function from package [`crypto/rand`](https://golang.org/pkg/crypto/rand/) to generate a [universally unique identifier](https://en.wikipedia.org/wiki/Universally_unique_identifier):

    b := make([]byte, 16)
    _, err := rand.Read(b)
    if err != nil {
            log.Fatal(err)
    }
    uuid := fmt.Sprintf("%x-%x-%x-%x-%x", b[0:4], b[4:6], b[6:8], b[8:10], b[10:])

Note that his UUID doesn't conform to [RFC 4122](https://tools.ietf.org/html/rfc4122). In particular, it doesn't contain any version or variant numbers.

The `rand.Read` call returns an error if the underlying system call fails. For instance if the runtime can't read `/dev/urandom` on a \*nix system or if [`CryptAcquireContext`](<https://msdn.microsoft.com/en-us/library/windows/desktop/aa379886(v=vs.85).aspx>) fails on a Windows system.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
