# Backtracking:

> Pseudo Code:
> 1. check if feasable sol (add it if so)
> 2. iterate over all availabe next options
> 3. for each, add it to the sol and recurse.
> 4. remove it from sol, and iterate to next option
```
def backtracking(candidates, target):
    res = []
    def helper_funciton(candidates: List[int], target: int, arr: List[int]):
        if valid_sol:
            if target == 0:
                res.append(arr[:])
            return

        for i in range(0, len(candidates)):
            arr.append(candidates[i])
            recur(candidates[i:], target - candidates[i], arr)
            arr.pop()

    helper_funciton(candidates, target, [])
    return res
```


#  BFS Backtracking of powerset of nums
Note that every subset should be present only once, to do so, we increase every exisiting subset with numbers which follows in the arrary.

## option 1

```
def subsets(self, nums: List[int]) -> List[List[int]]:
    
    queue = [[[x,y]] for x,y in enumerate(nums)]
    res = []
    while len(queue) >0:
        current = queue.pop(0)
        res.append([x[1] for x in current])               
        for i in range(current[-1][0]+1, len(nums)):
            queue.append(current + [[i,nums[i]]])
    
    return [[]] + res
```

## option 2 - bit mask manipulation
see [LeetCode](https://leetcode.com/problems/subsets/solution/)

## option 3 - BFS
```
def subsets(self, nums: List[int]) -> List[List[int]]:
    n = len(nums)
    output = [[]]
    
    for num in nums:
        output += [curr + [num] for curr in output]
    
    return output
```
