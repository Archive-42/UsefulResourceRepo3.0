<span class="underline"></span>

<span class="underline"></span>

Hash Tables
-----------

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  Robin Hood Hashing
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

Resources
---------

[Robin Hood Hashing](https://cs.uwaterloo.ca/research/tr/1986/CS-86-14.pdf) (pdf)  
<span style="color: grey; font-style: italic; font-size: smaller">by Pedro Celis</span>

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

Robin Hood Hashing
==================

Robin Hood hashing is a technique for implementing hash tables. It is based on [open addressing](hash-tables-open-addressing.html) with a simple but clever twist: As new keys are inserted, old keys are shifted around in a way such that all keys stay reasonably close to the slot they originally hash to. In particular, the **variance** of the keys distances from their "home" slots is minimized.

Key properties include:

-   Lookup is *O*(1) ammortized and *O*(ln *n*) in worst case
-   Fast also when looking up keys that does not exist
-   Minimal variance on distances to "home" slots
-   Cache friendly and memory efficient (no linked lists or additional pointers)
-   Performes well under load factors as high as ~0.9

☞

Make sure you have a basic understanding of hash tables in general (see [Hash Tables](hash-tables.html)), and of open addressing in particular (see [Open Addressing](hash-tables-open-addressing.html)).

Probe Sequence Lengths
----------------------

The algorithm is based on the notion of **probe sequence lengths** (PSL). The PSL of a key is the number of probes required to find the key during lookup.

A key with a low PSL can be thought of as rich, and a key with a high PSL can be thought of as poor. When inserting a new key the algorithm moves the rich in favor of the poor (“takes from the rich and gives to the poor”), hence the name Robin Hood hashing.

Insertion
---------

If the slot that the key hashes to is empty, we insert the key there and return. If not, we start probing for an empty slot. When encountering an occupied slot we compare the PSL of the existing key, with the PSL that the new key would have if inserted in that slot. If the new key has a higher PSL it is "poorer" and it would be unfair to let go on further, so we swap: The new key is inserted, and the existing key is taken out and is now the key to insert. The probing continues until an empty slot is found.

**Example:** Insertion of key 76 which hashes to the third slot. The PSL for a key is shown below to the right.

43 -1 0 1 2 17 0 1 2 3 31 0 1 2 3 10 0 1 2 3 28 1 2 3 4 Key to insert: 76 -1 0 1 2 Lower PSL → Move on! Same PSL → Move on! Higher PSL → Swap! Same PSL → Move on! Free slot Insert!

Lookup
------

The simplest strategy is to look for the key in the slot to which it hashes, and if not found, follow the probing sequence. The probing terminates when an empty slot is found, or a key is encountered which has a PSL higher than the sought key would have in that slot. (If the sought key had been in the table, it would have been located before that key.)

### Starting in the middle

The probability of finding a key is the slot it originaly hashed to is low. In fact, the probability of finding the key a certain number of steps into the probe sequence is higher. A simple optimization is therefore to keep track of the overall mean PSL, and probe up and down from that value. The sequence to probe would look as follows:

*mean*, <span class="no-wrap">*mean* − 1</span>, <span class="no-wrap">*mean* + 1</span>, <span class="no-wrap">*mean* − 2</span>, <span class="no-wrap">*mean* + 2</span>, …

This technique is called **smart search**.

### Optimal probe order

The distribution of keys is not uniform around the mean however, so there's still room for improvement. By keeping track of the distributions of the PSLs, one can probe the slots in order of decreasing probability. The technique is called **organ-pipe search**.

As an example, the [original paper](https://cs.uwaterloo.ca/research/tr/1986/CS-86-14.pdf) on Robin Hood hashing gives the following distribution for a nearly full table:

Probability Probe Position 0.1 0.2 0.3 0.4

While this approach improves slightly on the average number of probes, it requires keeping track of the distribution which incures a constant time overhead and a logarithmic memory overhead.

It should also be noted that both smart search and organ-pipe search hop back and forth in memory, so neither of them utilize the cache very well.

Removal
-------

As with normal open addressing, you can't simply clear out a slot, as that could cause future lookups to fail. You can mark slots as deleted (create so called tombstones, see [Hash Tables: Open Addressing](hash-tables-open-addressing.html)) but Robin Hood hashing lends itself to an even better technique, called **backward shifting**.

Backward shifting works as follows: The slot holding the key to remove is cleared out. The algorithm then starts shifting the keys in the following slots back one step to fill the gap. The backward shifting continues until a key is encountered with PSL 0 (since it would would be shifted before the slot it hashes to), or an empty slot is found.

**Example:** The key 15 is to be removed from the hash table below.

48 -1 0 1 2 15 0 1 2 3 33 0 1 2 3 19 1 2 3 4 92 -1 0 1 2 72 0 1 2 3 Key to remove → Clear slot → PSL &gt; 0 Shift back! PSL &gt; 0 Shift back! PSL = 0 Done!

The reason why this works in Robin Hood hashing is because **the keys are always sorted according to the index of the slot they originally hash to**. Here's an illustration:

Slots that keys originally hash to Slots where keys are stored in a Robin Hood hash table 14 7,23,4 6,71 58 58 14 7 23 4 6 71 Invariant: Arrows will never cross each other

**A note on tombstones**

The [original paper](https://cs.uwaterloo.ca/research/tr/1986/CS-86-14.pdf) suggests using tombstones. While it does provide better performance for removal, it comes with the same drawbacks as when used in standard open addressing. Lookup and insert algorithm gets slightly more complex, and the tombstones causes slightly longer chains (higher PSLs).

In Robin Hood hashing, there's a clever trick to mitigate the performance impact due to longer chains. By keeping track of the global min and max PSL, one can limit the probing to that range. The probing can be started min steps into the sequence, and stop early at the max value.

Probing techniques
------------------

Different probing techniques usually provide a trade-off between memory locality and avoidance of clustering. Since Robin Hood hashing is relatively resilient to clustering (both primary and secondary), linear probing—the most cache-friendly alternative—is typically used.

Complexity
----------

The worst case runtime complexity is *O*(*n*) for all operations. As usual however, the more interesting analysis is on the expected runtime.

With smart search, or organ pipe search, the expected lookup time is *O*(1). The expected length of the **longest PSL** (and thus the expected runtime complexity of lookup, remove and insert) in a full table is Θ(ln *n*).

With linear probing the variance of all probe lengths is minimized. In a full table the variance is Θ(*n*) which is in fact optimal among all open addressing techniques that do not look ahead in the table.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
