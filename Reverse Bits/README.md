Single Number
==========

## C++


```cpp
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t r(0);
        for(int i(0); i < 32; ++i)
        {
            r <<= 1;
            r |= n & 1;
            n >>= 1;
        }
        return r;
    }
};
```
Better
```cpp
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        n = (n << 16) | (n >> 16);
        n = ((n & 0x00ff00ff) << 8) | ((n & 0xff00ff00) >> 8);
        n = ((n & 0x0f0f0f0f) << 4) | ((n & 0xf0f0f0f0) >> 4);
        n = ((n & 0x33333333) << 2) | ((n & 0xCCCCCCCC) >> 2);
        n = ((n & 0x55555555) << 1) | ((n & 0xAAAAAAAA) >> 1);
        return n;
    }
};
```
