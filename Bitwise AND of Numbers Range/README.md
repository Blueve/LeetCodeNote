Bitwise AND of Numbers Range
==========

## C++


```cpp
class Solution {
public:
    int rangeBitwiseAnd(int m, int n) {
        int i;
        for(i = 0; m && m != n; ++i)
        {
            m >>= 1;
            n >>= 1;
        }
        return m << i;
    }
};
```
