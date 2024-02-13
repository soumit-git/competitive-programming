# 1154. Day of the Year
Given a string date representing a Gregorian calendar date formatted as YYYY-MM-DD, return the day number of the year.

 

Example 1:

Input: date = "2019-01-09"
Output: 9
Explanation: Given date is the 9th day of the year in 2019.
Example 2:

Input: date = "2019-02-10"
Output: 41
 

Constraints:

date.length == 10
date[4] == date[7] == '-', and all other date[i]'s are digits
date represents a calendar date between Jan 1st, 1900 and Dec 31th, 2019.

## Solution
```
class Solution:
    def dayOfYear(self, date: str) -> int:
        d = date.split('-')
        res = 0

        year = int(d[0])
        month = int(d[1])
        day = int(d[2])
        leap_year = 0

        if (year % 400 == 0) and (year % 100 == 0):
          leap_year = 1
        elif (year % 4 ==0) and (year % 100 != 0):
          leap_year = 1

        days_in_month = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]

        for i in range(month - 1):
          res += days_in_month[i]
        
        res = res + day + leap_year
        res -= leap_year if month <= 2 else 0

        return res
```