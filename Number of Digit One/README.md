Number of Digit One
==========

## C++


```cpp
class Solution {
public:
    int countDigitOne(int n) {
        int count(0);
        for(long m = 1; m <= n; m *= 10)
        {
            int a = n / m; // Left part
            int b = n % m; // Right part
            // left / 10 * m --> not considering leading with 1 => xxx[^1]|xxxx
            //+(left % 10 == 1 ? right + 1 : 0) --> considering leading with 1 => xxx[1]|xxxx
            // 
            // xxx[2-9]|xxxx should have extra m one, then first part to
            // (left + 8) / 10 * m
            // which when fisrt unit of left is bigger than 1, it will add extra m one.
            count += (a + 8) / 10 * m + (a % 10 == 1 ? b + 1 : 0);
        }
        return count;
    }
};
```
