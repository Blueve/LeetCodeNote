Add Binary
==========

## C++


```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && !(n & (n - 1));
    }
};
```
