# Perturbations:

```
import collections
import itertools
print(list(itertools.permutations([1, 2, 3])))

def perturbation(elements):
    if len(elements) == 1:
        yield elements
        return
    
    for i in range(0, len(elements)):
        for pert in perturbation(elements[:i] + elements[i+1:]):
            yield [elements[i]] + pert

def permute(self, nums: List[int]) -> List[List[int]]:
    res = []
    def helper(nums, arr):
        if len(nums) == 0:
            res.append(arr)

        for i in range(0, len(nums)):
            helper(nums[:i] + nums[i+1:], arr + [nums[i]])

    helper(nums,[],)
    return res
```

> In the follwoing `permuteUnique` we will use Counter dictionary, and use backtrack method.
Every iteration select one remaining characther and increase the size of `comb`, this approach results with fewer iterations, as there isn't importence for which '1' has begun first.

```
def permuteUnique(self, nums: List[int]) -> List[List[int]]:
    results = []
    def backtrack(comb, counter):
        if len(comb) == len(nums):
            # make a deep copy of the resulting permutation,
            # since the permutation would be backtracked later.
            results.append(list(comb))
            return

        for num in counter:
            if counter[num] > 0:
                # add this number into the current combination
                comb.append(num)
                counter[num] -= 1
                # continue the exploration
                backtrack(comb, counter)
                # revert the choice for the next exploration
                comb.pop()
                counter[num] += 1

    backtrack([], Counter(nums))

    return results
```





# Substring Templates

```
def findSubstring(str s):
    begin, end = 0,0
    d = 0

    # 1. initialize hash map
    map = collections.Counter(s) # collections.defaultDict(int)

    while end < len(s):
        if map[s[end++]]-- : 
            #modify counter
        
        while #counter condition :
            # update d here if finding minimum*/

            # increase begin to make it invalid/valid again

            if(map[s[begin++]]++ ?){ /*modify counter here*/ }

        #update d here if finding maximum*/
    return d
```
# String manipulation

use 26 bit mask, and update it with each charachter.
use & or | operators to find joined or distinct charachters
```
mask = 0
for c in word:
  mask |= (1 << (ord(c) - ord('a')))
```


# Interval
## Techniques
> Sort the array of intervals by its starting point
A common routine for interval questions is to sort the array of intervals by each interval's starting value. This step is crucial to solving the Merge Intervals question.

> Checking if two intervals overlap:
```
def is_overlap(a, b):
  return a[0] < b[1] and b[0] < a[1]
```
> Merging two intervals:
```
def merge_overlapping_intervals(a, b):
  return [min(a[0], b[0]), max(a[1], b[1])]
```


#mergre of 2 sorted arrays

[LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/)

[YouTube explanation](
https://www.youtube.com/watch?v=q6IEA26hvXc&t=1006s&ab_channel=NeetCode)

# Priority Qeue
> find median using min heap and maxheap
Algorithm:

> 1. create small, large priority queues (max heap, min heap respectivly), each one will conatian roughly half of the items in the stream
> 2. insert new elements to small queue
> 3. if there exists an element in samll which is larger than elemnt in large queue, pop and push to large queue ( O(1), as the samll is max queue, and large in min queue)
> 4. if the lengths of queue is not roughly the same size (diff of up to one), pop from the bigger queue to the queue with fewer elements
> 5. calculating median:
    * if both queues have same length, take the root of both and return thier avarage.
    * if one queue is greater than the other, takes its root


# variations of 8 queens
Learned in Intro to AI (236350) efficient way using local search