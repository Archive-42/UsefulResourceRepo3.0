



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

# Java: Ellipsizing strings

This algorithm treats "thin" characters (i, I, l, 1 etc) as ½ character, and respects word boundries. It's good enough in most cases and has no dependency on `FontMetrics` or other AWT/Swing classes.

    private final static String NON_THIN = "[^iIl1\\.,']";

    private static int textWidth(String str) {
        return (int) (str.length()
                - str.replaceAll(NON_THIN, "").length() / 2);
    }

    public static String ellipsize(String text, int max) {

        if (textWidth(text) <= max)
            return text;

        // Start by chopping off at the word before max.
        // This is an over-approximation due to thin-characters.
        int end = text.lastIndexOf(' ', max - 1);

        // Just one long word? Chop it off.
        if (end == -1)
            return text.substring(0, max - 1) + "…";

        // Step forward as long as textWidth allows
        int newEnd = end;
        do {
            end = newEnd;
            newEnd = text.indexOf(' ', end + 1);

            // No more spaces
            if (newEnd == -1)
                newEnd = text.length();

        } while (textWidth(text.substring(0, newEnd) + "…") < max);

        return text.substring(0, end) + "…";
    }

## Test

lorem…  
lorem ipsum…  
lorem ipsum dolor sit…  
lorem ipsum dolor sit amet,…  
lorem ipsum dolor sit amet,…  
lorem ipsum dolor sit amet, consectetur…  
lorem ipsum dolor sit amet, consectetur adipiscing…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna.…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum,…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper venenatis,…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper venenatis, magna odio…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper venenatis, magna odio…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper venenatis, magna odio volutpat velit,…  
lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam non enim magna. Morbi dictum, velit vel semper venenatis, magna odio volutpat velit, at…

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
