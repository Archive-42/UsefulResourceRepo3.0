<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Command-line arguments](command-line-arguments.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Read a file line by line](read-file-line-by-line.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Regular expressions](regexp-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Write log to file](log-to-file.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Access environment variables](environment-variables.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

Go: Write a command-line (CLI) application
==========================================

This example is a simplified version of the Unix `grep` command. The program searches the input file for lines containing the given pattern and prints these lines.

    func main() {
            log.SetPrefix("grep: ")
            log.SetFlags(0) // no extra info in log messages

            if len(os.Args) != 3 {
                    fmt.Printf("Usage: %v PATTERN FILE\n", os.Args[0])
                    return
            }

            pattern, err := regexp.Compile(os.Args[1])
            if err != nil {
                    log.Fatalln(err)
            }

            file, err := os.Open(os.Args[2])
            if err != nil {
                    log.Fatalln(err)
            }
            defer file.Close()

            scanner := bufio.NewScanner(file)
            for scanner.Scan() {
                    line := scanner.Text()
                    if pattern.MatchString(line) {
                            fmt.Println(line)
                    }
            }
            if err := scanner.Err(); err != nil {
                    log.Println(err)
            }
    }

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
