



## Further Reading

[Generate a random number in a given range](generate-number-random-range.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Generate a random string (password, booking reference)](generate-random-string-password-booking-reference.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Generate a random UUID (GUID)](generate-uuid-guid.html)  
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

# Go: Cryptographically secure random numbers

Go has two packages for random numbers:

- [`math/rand`](https://golang.org/pkg/math/rand/) implements a large selection of pseudo-random number generators.
- [`crypto/rand`](https://golang.org/pkg/crypto/rand/) implements a cryptographically secure pseudo-random number generator with a limited interface.

The two packages can be combined by calling [`rand.New`](https://golang.org/pkg/math/rand/#New) in package `math/rand` with a source that gets its data from `crypto/rand`.

    import (
            crand "crypto/rand"
            rand "math/rand"

            "encoding/binary"
            "fmt"
            "log"
    )

    func main() {
            var src cryptoSource
            rnd := rand.New(src)
            fmt.Println(rnd.Intn(1000)) // a random number from 0 to 999
    }

    type cryptoSource struct{}

    func (s cryptoSource) Seed(seed int64) {}

    func (s cryptoSource) Int63() int64 {
            return int64(s.Uint64() & ^uint64(1<<63))
    }

    func (s cryptoSource) Uint64() (v uint64) {
            err := binary.Read(crand.Reader, binary.BigEndian, &v)
            if err != nil {
                    log.Fatal(err)
            }
            return v
    }

The `crand.Reader` returns an error if the underlying system call fails. For instance if the runtime can't read `/dev/urandom` on a \*nix system or if [`CryptAcquireContext`](<https://msdn.microsoft.com/en-us/library/windows/desktop/aa379886(v=vs.85).aspx>) fails on a Windows system.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
