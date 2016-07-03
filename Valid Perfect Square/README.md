Valid Perfect Square
==========

## C++


```cpp
class Solution {
public:
    bool isPerfectSquare(int num) {
        long l = 0, r = num, m;
        while(l <= r)
        {
            m = l + (r - l >> 1);
            long square = m * m;
            if(square > num)
                r = m - 1;
            else if(square < num)
                l = m + 1;
            else
                return true;
        }
        return false;
    }
};
```
