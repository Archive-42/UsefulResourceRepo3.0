<span class="underline"></span>

<span class="underline"></span>

## References

[Javadoc for List.toArray](https://docs.oracle.com/javase/8/docs/api/java/util/List.html#toArray-T:A-)  
<span style="color: grey; font-style: italic; font-size: smaller">docs.oracle.com</span>

[Arrays of Wisdom of the Ancients](https://shipilev.net/blog/2016/arrays-wisdom-ancients/)  
<span style="color: grey; font-style: italic; font-size: smaller">by Aleksey Shipilёv</span>

<span class="underline"></span>

## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

# Java: Passing a list as argument to a vararg method

Use [`List.toArray(T[] arr)`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#toArray-T:A-):

    yourVarargMethod(yourList.toArray(new String[0]));

(Replace `String` with whatever type of objects your list contains.)

## Details

`String...` behaves similarly to `String[]`.

You could also use `new String[yourList.size()]` instead of `new String[0]`. [This is however _not_ more performant.](https://shipilev.net/blog/2016/arrays-wisdom-ancients/)

## Full Example

    import java.util.List;
    class Demo {

        public static void main(String[] args) {
            List<String> yourList = List.of("hello", "world");
            yourVarargMethod(yourList.toArray(new String[0]));
        }

        static void yourVarargMethod(String... args) {
            for (String str : args) {
                System.out.println(str);
            }
        }
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
