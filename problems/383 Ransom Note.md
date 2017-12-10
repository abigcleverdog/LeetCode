```
Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

Note:
You may assume that both strings contain only lowercase letters.

canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true

```
my thoughts:
```
1. for each char in 'str1', ->
   check if it exists in 'str2' ->
	if yes, mark off the index in 'str2' for future search ->
	if no, ->
	return False.
   all yeses, ->
   return True.
   O(n^2)
2. convert 'str1' to a dict of (char, freq) ->
   for each char in 'str2', ->
	if len(dict)==0, return True ->
	if char is in the dict, ->
		if dict[char] = 1, dict.pop(char) ->
		else dict[char] -= 1.
   after loop, if len(dict)==0, return True ->
   else return False.
   O(n+n*c) = O(n)
3. I do not think I can do better than linear run time
   as I need to go through char in 'str1' for sure.
   There may be some tweak to save time in special cases,
   such as str1 is longer than str2.
```
   
my solution:
```
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        if len(ransomNote) == 0:
            return True
        
        r = {}
        
        for c in ransomNote:
            r[c] = 1 if c not in r else r[c]+1
        
        for c in magazine:
            if c in r:
                if r[c] == 1:
                    r.pop(c)
                else:
                    r[c] = r[c] - 1
            if len(r) == 0:
                return True
        return False
```

my comments:
solution accepted, 66ms run time
from other ppl's solution:
1. convert 'str1' to a dict of (char,count):
`collections.Counter(str1)`
2. operation on collections.Counter:
collections.Counter1 - collections.Counter2
is True, if anything left over cc1
3. It may be more precise to use O(m+n) instead of O(n)
in this case.
