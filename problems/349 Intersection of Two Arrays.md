```
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

Note:
Each element in the result must be unique.
The result can be in any order.
```
my thoughts:
```
1. for each value in 'nums1', ->
   check if it exists in 'nums2' ->
   if yes, append it to the result ->
   return result.
   O(n^2)
2. convert 'nums1' to a hash table (Set) with no repeating value, ->
   for each value in 'nums2', check if it is in the table ->
   if yes, append it to the result ->
   return result.
   O(n+n*c) = O(n)
3. sort 'nums1' ->
   for each value in 'nums2', binary search to check if it is in 'nums1' ->
   if yes, append it to the result ->
   return result.
   O(n*lg(n)+n*lg(n)) = O(n*lg(n))
```

my solution:
```
class Solution(object):
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        s = set()
        res = set()
        
        for n in nums1:
            if n not in s:
                s.add(n)
        
        for n in nums2:
            if n in s and n not in res:
                res.add(n)
                
        return list(res)

```

my comments:
solution accepted, 45ms run time
from other ppl's solution:
1. convert list 'nums1' to set:
`set(nums1)`
2. list of intersection of set A & set B:
list(set(nums1) & set(nums2))
