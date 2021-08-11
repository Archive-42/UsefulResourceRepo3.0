## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  Hash Table vs Hash Set
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# Hash Table

# Hash Set

A hash table (or hash map) is an implementation of a **map** ADT.

A hash set is an implementation of a **set** ADT.

You can add **mappings** from keys to values, and later retrieve values associated with keys.

You can add values, and later check for containment.

    phoneBook.put("Alice", "+123456789")
    ...
    ...phoneBook.get("Alice")...

    people.add("Alice")
    ...
    if (people.contains("Alice"))
        ...

A hash table stores key-value pairs. The hashing is based on the key.

A hash set stores values. The value is also the key, i.e. the hashing is based on the value.

**Note:** The literature on these types of data structures (including many of the articles here on Programming.Guide) mostly focus on hash sets rather than hash tables. This is because the actual values are never really relevant to the discussion, and it's easy to generalize an implementation that works only with keys, into one that works with key-value pairs.

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
