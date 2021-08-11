



## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](java/index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

# Generating competition rankings

Descriptions of the various ranking strategies can be found here: [Wikipedia: Ranking](https://en.wikipedia.org/wiki/Ranking)

## Standard competition ranking, "1224"

Idea: Start with ranking 1, assign same as previous if score is equal, otherwise assign `index + 1`.

    // scores = [10, 15, 15, 20]  (sorted)
    int[] rankings = new int[scores.length];
    rankings[0] = 1;
    for (int i = 1; i < rankings.length; i++)
        rankings[i] = scores[i] == scores[i - 1] ? rankings[i - 1] : i + 1;
    // rankings = [1, 2, 2, 4]

## Modified competition ranking, "1334"

Idea: Same as above, but start from the end:

    int[] rankings = new int[scores.length];
    rankings[scores.length - 1] = scores.length;
    for (int i = rankings.length - 2; i >= 0; i--)
        rankings[i] = scores[i] == scores[i + 1] ? rankings[i + 1] : i + 1;
    // rankings = [1, 3, 3, 4]

## Dense ranking, "1223"

Idea: Increment ranking only if current score differs from previous:

    int[] rankings = new int[scores.length];
    rankings[0] = 1;
    for (int i = 1, r = 1; i < rankings.length; i++)
        rankings[i] = scores[i] == scores[i - 1] ? r : ++r;
    // rankings = [1, 2, 2, 3]

## Ordinal ranking, "1234"

Trivial: Ranking equals `index + 1`.

The key desirable property in ordinal ranking is that it's [stable](https://en.wikipedia.org/wiki/Sorting_algorithm#Stability). Luckily [`Arrays.sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-int%3AA-), [`Collections.sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#sort-java.util.List-) and [`List.sort`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html#sort-java.util.Comparator-) are all stable.

## Fractional ranking, "1 2½ 2½ 4"

    List<Integer> clusters = new ArrayList<>();
    clusters.add(1);
    for (int i = 1; i < scores.length; i++) {
        if (scores[i] == scores[i - 1]) {
            int last = clusters.size() - 1;
            clusters.set(last, clusters.get(last) + 1);
        } else {
            clusters.add(1);
        }
    }
    double[] rankings = new double[scores.length];
    int index = 0;
    for (int cluster : clusters) {
        double ranking = index + (1 + cluster) / 2.0;
        Arrays.fill(rankings, index, index += cluster, ranking);
    }
    // rankings = [1, 2.5, 2.5, 4]

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
