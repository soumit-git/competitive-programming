# 1073. Adding Two Negabinary Numbers
Given two numbers arr1 and arr2 in base -2, return the result of adding them together.

Each number is given in array format:  as an array of 0s and 1s, from most significant bit to least significant bit.  For example, arr = [1,1,0,1] represents the number (-2)^3 + (-2)^2 + (-2)^0 = -3.  A number arr in array, format is also guaranteed to have no leading zeros: either arr == [0] or arr[0] == 1.

Return the result of adding arr1 and arr2 in the same format: as an array of 0s and 1s with no leading zeros.

 

Example 1:

Input: arr1 = [1,1,1,1,1], arr2 = [1,0,1]
Output: [1,0,0,0,0]
Explanation: arr1 represents 11, arr2 represents 5, the output represents 16.
Example 2:

Input: arr1 = [0], arr2 = [0]
Output: [0]
Example 3:

Input: arr1 = [0], arr2 = [1]
Output: [1]
 

Constraints:

1 <= arr1.length, arr2.length <= 1000
arr1[i] and arr2[i] are 0 or 1
arr1 and arr2 have no leading zeros

## Solution

```python

class Solution:
    def addNegabinary(self, arr1: List[int], arr2: List[int]) -> List[int]:
        def decrypt(arr):
          n = len(arr)
          res = 0
          for i in range(n):
            if arr[i]:
              res += (-2) ** (n - i -1)
          return res
        
        def encrypt(num):
          res = []
          if num == 0:
            return [0]
          
          while num:
            num, rem = divmod(num, -2)
            if rem < 0:
              rem += 2
              num += 1
            res.append(rem)
          return res[::-1]

        return encrypt(decrypt(arr1) + decrypt(arr2))
```