# Sliding window

To identify problems where a sliding window can be helpful, look for a few properties:

 - Whenever you need to calculate a running average
- If you want to formulate a set of adjacent pairs
- The problem involves an ordered data structure
- If you need to identify a target value in an array
- If you need to identify a longest, shortest, or most optimal sequence that satisfies a given condition in a collection (substring, subarray)
- The problem input is a linear data structure such as a linked list, array, or string

-----------------------

1. iterate only on available data (e.g do not slip with the window edge over the edge of the array)
2. jump:
  - the window may be consists of block, if so, it might help to manage each block independently 
  - if the block validtion fails, consider skip the block and set window left edge to the block's right edge.


----------------

in Letcode it often uses the following pattern:
In any sliding window based problem we have two pointers. One right pointer whose job is to expand
   the current window and then we have the left pointer whose job is to contract a given window.
   At any point in time only one of these pointers move and the other one remains fixed.

> 1. Use two pointers: start and end to represent a window.
> 2. Move end to find a valid window.
> 3. When a valid window is found, move start to find a smaller window.

 - dic_t         - Dictionary which keeps a count of all the unique characters in t.
 - window_counts - Dictionary which keeps a count of all the unique characters in the current window.
 - usually there are two while loops (the outer one involving the right <= len(s))
   inner one for (left <= right and condition).

 the condition usualy responsible to reduce the window_size while maintaining feasible sol.
 (in questions where the window is fixed, the condition might be something else)
 inside the inner while loop (as left decreases), we update the window_counts accordingly
