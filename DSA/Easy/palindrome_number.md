## Palindrome number
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x<0:
            return False
        copy = x
        new_num =0
        while x>0:
            r = x%10
            x = x//10
            new_num = new_num*10 + r
        
        if new_num == copy:
            return True
        return False
```
