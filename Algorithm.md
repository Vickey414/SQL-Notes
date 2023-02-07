

## Binary Search 
```python
class Solution(object):
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        def search1st(nums, target):
           N = len(nums)
           start, end = -1,-1
           left, right = 0, N
           # binary search left
           while left < right:
               mid = (left+right) // 2
               if nums[mid] >= target:
               # 当中间的数值大于或等于target时，那么说明左边可能还会有与target相等的，这里我们想要找出left index，所以移动right到mid
                   right = mid
               else: left = mid +1
               我们会不断地更新
           if left < N and nums[left] == target:
               start = left
           
           # binary search right
           left, right = 0, N
           while left < right:
               mid = (left+right) // 2
               if nums[mid] <= target:
                   left = mid + 1
               else: right = mid
           if nums[right - 1] == target: end = right - 1
           return [start, end]
 ```



            
