# Two Pointers

## Cycle Detection (Floyd algorithm)

Have two pointers, where fast pointer is incremented twice as much as the slow pointer, if the two pointers meet, it means a cycle exists. 

  * Find entry point of the cycle by Floyd algorithm, see approach 7 @ [leetcode](https://leetcode.com/problems/find-the-duplicate-number/solution/)
  * Two phases:
    * Phase 1 - fast pointer travels twice as the slow pointer until collision.
    * Phase 2 - 
      * reset the fast pointer to the begining of the path, now both pointers are incremented by same amoumt of 1.
      * The first occurance  is the cycle entry point.


## Additional Topics

Two pointer approaches are also common for linked lists. This approach is used for many classic linked list problems.
* Getting the kth element from last node - Have two pointers, where one(A) is the first node in the list, and the other (B) is k nodes ahead of the other. When node B reaches the end of the list, the node A is k nodes behind.
*  Getting the middle node - Have two pointers, where one pointer is incremented twice as much as the other. When the faster node reaches the end of the list, the slower node will be at the middle.
