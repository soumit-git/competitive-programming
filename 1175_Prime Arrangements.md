# 1175. Prime Arrangements
Return the number of permutations of 1 to n so that prime numbers are at prime indices (1-indexed.)

(Recall that an integer is prime if and only if it is greater than 1, and cannot be written as a product of two positive integers both smaller than it.)

Since the answer may be large, return the answer modulo 10^9 + 7.

 

Example 1:

Input: n = 5
Output: 12
Explanation: For example [1,2,5,4,3] is a valid permutation, but [5,2,3,4,1] is not because the prime number 5 is at index 1.
Example 2:

Input: n = 100
Output: 682289015
 

Constraints:

1 <= n <= 100

## Solution
```
class Solution:
    def numPrimeArrangements(self, n: int) -> int:
        def is_prime(num):
          if num == 1:
            return False
          for i in range(2, num // 2 + 1):
            if num % i == 0:
              return False
          return True
        
        MOD = 10 ** 9 + 7
        prime = 0

        for i in range(1, n + 1):
          prime += 1 if is_prime(i) else 0
        
        def fac(x):
          f = 1
          while x > 0:
            f = (f * x) % MOD
            x -= 1
          return f
        
        return fac(n - prime) * fac(prime) % MOD
```