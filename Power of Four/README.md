Power of Four
==========

## C++


```cpp
class Solution {
public:
    bool isPowerOfFour(int num) {
        if(num < 1 || (num & (num - 1)))
            return false;
        int cnt(0);
        while(!(num & 1))
        {
            num >>= 1;
            ++cnt;
        }
        return !(cnt & 1);
    }
};
```

Without using loop / recursion
```cpp
class Solution {
public:
    bool isPowerOfFour(int num) {
        // ... 0101b => ... 5h
        return num > 0 &&
               !(num & (num - 1)) &&
               num & 0x55555555;
    }
};
```