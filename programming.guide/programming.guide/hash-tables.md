<span class="underline"></span>

<span class="underline"></span>

Hash Tables
-----------

1.  Hash Tables
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
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

Related
-------

[Hash Table vs Hash Set](hash-table-vs-hash-set.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Amortized time complexity](amortized-time-complexity-analysis.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Big O notation explained](big-o-notation-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

Hash Tables
===========

Hash tables (also known as hash maps) are associative arrays, or dictionaries, that allow for fast insertion, lookup and removal regardless of the number of items stored.

Here’s an example of how they can be used:

    HashTable phoneBook = new HashTable()
    phoneBook.put("Adam", "(202) 555-0309")
    phoneBook.put("Beth", "(335) 754-1215")

    print("Adam’s number: " + phoneBook.get("Adam"))

Internally they are similar to card indexes: An item can be found quickly by first jumping to its approximate location, and then searching locally from there.

Representation
--------------

The simplest way to implement a hash table is to use an **array of linked lists**.

Each array cell is called a **bucket**, and each list node stores a **key-value pair**.

Following the analogy from the previous section, the array cells that can be accessed quickly can be thought of as index cards, and nodes in the list as data cards.

(k, v) Array of buckets Nodes of key-value pairs

Finding the right bucket
------------------------

Which bucket a given key belongs to, is determined by a **hash function** as follows…

*bucket index* = hash(*key*) % length(*bucket array*)

…where % denotes the remainder operator.

For efficiency reasons, an additional variable is used to keep track of the current total number of key-value pairs.

☞

There are other ways to implement hash tables, but this is the representation that will be used here to introduce the subject. See section [Other Collision Resolution Strategies](hash-tables.html#other-impl) for alternatives.

Insertion
---------

Here's how a mapping from key `k` to value `v` is inserted in a hash table:

1.

Rehash if load factor is too high. (Explained in separate section.)

rehash\_if\_needed()

2.

Compute the hash for the key

h = hash(k)

3.

Use remainder operator to compute the bucket index

i = h % length(buckets)

4.

Look for key among existing nodes.  
  
If found update value of existing node.

last = NULL  
n = buckets\[i\]  
while n ≠ NULL:  
    if n.key == k:  
        n.value = v  
        return  
    last = n  
    n = n.next

5.

If not found, append new node to list

new\_node = new Node(k, v)  
if last == NULL:  
    bucket\[i\] = new\_node  
else:  
    last.next = new\_node

Insert (new key) Insert (update existing key) k,v Wrong key Key not found Append new node Update value Key found \# First (new) k, v k ,v \# Second (new) k, v k ,v \# First (update) k, v k ,v \# Second (update) k, v k ,v \# Third k, v k , v

Lookup
------

Here's how the value for a key `k` is retrieved from a hash table:

1.

Compute the hash for the key

h = hash(k)

2.

Use remainder operator to compute the bucket index

i = h % length(buckets)

3.

Search through bucket linearly

n = buckets\[i\]  
while n ≠ NULL:  
    if n.key == k:  
        return n.value  
    n = n.next  
return NOT\_FOUND

Wrong key Key found Return value \# First k, v k ,v \# Second k, v k ,v \# Third k, v k , v

Remove
------

Here's how a key-value pair is removed from a hash table:

1.

Compute the hash for the key

h = hash(k)

2.

Use remainder operator to compute the bucket index

i = h % length(buckets)

3.

Search through bucket linearly to find key

last = NULL  
n = buckets\[i\]  
while n ≠ NULL:  
    if n.key == k:  
        if last == NULL:  
            buckets\[i\] = n.next  
        else:  
            last.next = n.next  
    n = n.next

Rehashing
---------

As the lengths of the linked lists grow, the average lookup time increases.

To keep the linked lists short and lookups fast, the number of buckets must be increased (and nodes redistributed). This is called **rehashing**.

1.

Allocate a new bucket array.

new\_size = 2 \* length(buckets)  
new\_buckets = new Bucket\[new\_size\]

2.

Reinsert all elements in new array.

for i in 0..buckets.length - 1:  
    while buckets\[i\] ≠ NULL:  
        n = buckets\[i\]  
        buckets\[i\] = n.next  
        h = hash(n.k)  
        i = h % new\_length  
        n.next = new\_buckets\[i\]  
        new\_buckets\[i\] = n  

3.

Replace old array with new array

buckets = new\_buckets

buckets new\_buckets

During rehashing the number of buckets is increased by some factor, typically 2. As shown in the article [Hash Tables: Complexity](hash-tables-complexity.html), it is important that the growth is exponential.

Traversal
---------

1.

For each bucket…

for i in 0..buckets.length - 1:

2.

…traverse each node

    n = buckets\[i\]:  
    while n ≠ NULL:  
        process(n)  
        n = n.next

Note that the order in which the key-value pairs are traversed is **unpredictable** due to the nature of hashing and rehashing.

Load Factor and Capacity
------------------------

The **load factor** is the average number of key-value pairs per bucket.

load factor

=

total number of key-value pairs

number of buckets

It is when the load factor reaches a given limit that rehashing kicks in. Since rehashing increases the number of buckets, it reduces the load factor.

The load factor limit is usually configurable and offers a **tradeoff between time and space costs**.

Lower limit More empty buckets More memory overhead Higher limit Larger buckets Slower lookups

The default load factor for a Java [`HashMap`](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) is 0.75 and for a C\# [`Hashtable`](https://docs.microsoft.com/en-us/dotnet/api/system.collections.hashtable?view=netframework-4.8) it’s 1.0.

The **capacity** is the maximum number of key-value pairs for the given load factor limit and current bucket count.

capacity

=

number of buckets

×

load factor limit

Since rehashing increases the number of buckets, it increases the capacity.

The default initial capacity for a Java [`HashMap`](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) is 12 and for a C\# [`Hashtable`](https://docs.microsoft.com/en-us/dotnet/api/system.collections.hashtable?view=netframework-4.8) it’s 0, i.e. the bucket array is initialized lazily upon first insertion.

**Example:** Here’s the structure of a hash table, configured with load factor limit of 4.

Current load factor: 24 / 8 = 3 Configured limit: 4 Current capacity: 8 × 4 = 32

Complexity Analysis
-------------------

As is clear from the way insert, lookup and remove works, the run time is proportional to the length of the linked lists. In worst case all keys hash to the same bucket, i.e. the whole data structure becomes equivalent to a linked list. This means that all operations run in *O*(*n*).

Assuming however that keys are dispersed evenly among the buckets, it can be shown that the complexity of the expected run time is *O*(1) for all operations.

See article [Hash Tables: Complexity](hash-tables-complexity.html) for a detailed analysis.

Other Collision Resolution Strategies
-------------------------------------

When two keys hash to the same bucket, i.e. when

hash(*k*<sub>1</sub>) ≡ hash(*k*<sub>2</sub>) (mod number of buckets)

it’s called a **collision**. The collision handling strategy described so far (one linked list per bucket) is an example of **closed addressing** using separate chains. Instead of linked lists, one can also use binary search trees, or as in the case of Java 9, a linked list up to a certain limit, and then convert it to a BST when more elements are added.

The alternative, **open addressing**, is to store all key-value pairs directly in the hash table array, i.e. there's at most one element per bucket. (The size of the array must always be at least as large as the number of elements stored.)

☞

See [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html) for a brief side-by-side comparison of the techniques or [Open Addressing](hash-tables-open-addressing.html) for details on open addressing.

A third option, which is more of theoretical interest but mentioned here for completeness, is to use a hash function that maps each key to slot of its own, and thus avoiding collisions all together. This is called **perfect hashing**.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
