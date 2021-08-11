<span class="underline"></span>

<span class="underline"></span>

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java: N-gram generation
=======================

Eagarly: Generating a list of n-grams
-------------------------------------

    public static List<String> ngrams(int n, String str) {
        List<String> ngrams = new ArrayList<String>();
        for (int i = 0; i < str.length() - n + 1; i++)
            ngrams.add(str.substring(i, i + n));
        return ngrams;
    }

**Example:** `ngrams(3,             "abcde")` = `["abc",             "bcd",             "cde"]`.

Lazily: Creating an iterator
----------------------------

    import java.util.Iterator;
    class NgramIterator implements Iterator<String> {
        private final String str;
        private final int n;
        int pos = 0;
        public NgramIterator(int n, String str) {
            this.n = n;
            this.str = str;
        }
        public boolean hasNext() {
            return pos < str.length() - n + 1;
        }
        public String next() {
            return str.substring(pos, pos++ + n);
        }
    }

**Example:**

    new NgramIterator(3, "abcde")
            .forEachRemaining(System.out::println);

prints

    abc
    bcd
    cde

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
