



## See also

[Switch Statement](switch-statement.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Switch Expression](switch-expression.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Enum Types](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Java™ Tutorials</span>

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



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

# Switch on enum (with examples)

Java has support for switching on enum values.

     Full contextswitch (month) {
        case FEB:
            System.out.println("28 days");
            break;
        case APR:
        case JUN:
        case SEP:
        case NOV:
            System.out.println("30 days");
            break;
        default:
            System.out.println("31 days");
    }enum Month {
        JAN, FEB, MAR, APR, MAY, JUN,
        JUL, AUG, SEP, OCT, NOV, DEC
    }

    public class EnumDemo {
        static void printNumDays(Month month) {
            switch (month) {
                case FEB:
                    System.out.println("28 days");
                    break;
                case APR:
                case JUN:
                case SEP:
                case NOV:
                    System.out.println("30 days");
                    break;
                default:
                    System.out.println("31 days");
            }
        }

        public static void main(String[] args) {
            printNumDays(Month.FEB); // 28 days
            printNumDays(Month.JUN); // 30 days
            printNumDays(Month.DEC); // 31 days
        }
    }

You must **not** fully qualify the constants. This will **not** compile: `case Month.FEB: …`

## Arrow Syntax

With Java 14+ the above switch statement can be written as:

    static void printNumDays(Month month) {
        switch (month) {
            case FEB -> System.out.println("28 days");
            case APR, JUN, SEP, NOV -> System.out.println("30 days");
            default -> System.out.println("31 days");
        }
    }

Or using a switch expression:

    static void printNumDays(Month month) {
        int days = switch (month) {
            case FEB -> 28;
            case APR, JUN, SEP, NOV -> 30;
            default -> 31;
        };
        System.out.println(days + " days");
    }

See [Switch Statement](switch-statement.html) and [Switch Expression](switch-expression.html) for more examples.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
