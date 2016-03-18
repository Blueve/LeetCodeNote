Counting Bits
==========

## C++


```cpp
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> result(num + 1, 1);
        result[0] = 0;
        int n(1), i(1);
        while(i <= num)
        {
            for(int j(0); j < n && i <= num ; ++i, ++j)
                result[i] += result[j];
            n <<= 1;
        }
        return result;
    }
};
```
Simpler
```cpp
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> result(num + 1, 0);
        result[0] = 0;
        
        for(int i(1); i <= num; ++i)
        {
            result[i] = result[i >> 1] + (i & 1);
        }
        return result;
    }
};
```