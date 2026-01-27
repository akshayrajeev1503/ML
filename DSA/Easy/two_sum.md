## TwoSum
> Solution using dictionary
> Time complexity - O(n)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = dict()

        for i, val in enumerate(nums):
            complement = target - val
            if complement in seen.keys():
                return i, seen[complement]

            seen[val] = i
```


        
