# Bucket sort (O(n))

```
def get_top_k(nums, k):
    counter = collections.Counter(nums)
    freq = [[] for i in range(0, len(nums)+1)]

    for n, times in counter.items():
        freq[times].append(n)

    res = []
    for i in range(len(freq)-1, 0, -1):
        for item in freq[i]:
            res.append(item)
            if len(res) ==k:
                return res
    
```