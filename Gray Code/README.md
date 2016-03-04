Gray Code
==========

## C++


```cpp
class Solution {
public:
    vector<int> grayCode(int n) {
        vector<int> result;
        int N(1 << n);
        for(int i(0); i < N; ++i)
        {
            result.push_back((i >> 1) ^ i);
        }
        return result;
    }
};
```
