## Related

[Hash Tables](hash-tables.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Hash Tables: Open Addressing](hash-tables-open-addressing.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  Open vs Closed Addressing
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

# Open Addressing

# Closed Addressing

Also known as **closed hashing**.

Also known as **open hashing**.

Collisions are dealt with by searching for **another empty buckets** within the hash table array itself.

A key is always stored in the bucket it's hashed to. Collisions are dealt with using **separate data structures** on a per-bucket basis.

At most one key per bucket.

Arbitrary number of keys per bucket.

Characteristic structure (colors denote "home" bucket):

<span style="color: #ccc">0</span>:  
<span style="color: red">1</span>: <span style="color: red">①</span>  
<span style="color: green">2</span>: <span style="color: green">②</span>  
<span style="color: #ccc">3</span>: <span style="color: green">②</span>  
<span style="color: maroon">4</span>: <span style="color: green">②</span>  
<span style="color: #ccc">5</span>: <span style="color: maroon">④</span>  
<span style="color: #ccc">6</span>:  
<span style="color: blue">7</span>: <span style="color: blue">⑦</span>  
<span style="color: #ccc">8</span>: <span style="color: blue">⑦</span>  
<span style="color: darkorange">9</span>: <span style="color: darkorange">⑨</span>

Characteristic structure (colors denote "home" bucket):

<span style="color: #ccc">0</span>:  
<span style="color: red">1</span>: <span style="color: red">①</span>  
<span style="color: green">2</span>: <span style="color: green">②②②</span>  
<span style="color: #ccc">3</span>:  
<span style="color: maroon">4</span>: <span style="color: maroon">④</span>  
<span style="color: #ccc">5</span>:  
<span style="color: #ccc">6</span>:  
<span style="color: blue">7</span>: <span style="color: blue">⑦⑦</span>  
<span style="color: #ccc">8</span>:  
<span style="color: darkorange">9</span>: <span style="color: darkorange">⑨</span>

Example techniques:

- Linear Probing
- Quadratic Probing
- Double hashing
- Hopscotch hashing
- Robin Hood hashing
- Cuckoo hashing
- 2-Choice hashing

Example techniques:

- Separate chaining using linked lists
- Separate chaining using dynamic arrays
- Using self-balancing binary search trees

Theoretical maximum load factor of 1.

No theoretical maximum load factor.

The size of the hash table array must always be at least as large as the number of keys in the hash table.

Performance degrades as load factor grows.

Benefits:

- No size overhead apart from the hash table array.
- Better memory locality and cache performance. All elements laid out linearly in memory.
- Performs better than closed addressing when the number of keys is known in advance and the churn is low.

Benefits:

- Easier removal (no need for deleted markings)
- Typically performs better with high load factor.
- No issues with clustering.

For more details on open addressing, see [Hash Tables: Open Addressing](hash-tables-open-addressing.html).

The most common closed addressing implementation uses separate chaining with linked lists. This approach is described in detail the [introductory article](hash-tables.html).

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
