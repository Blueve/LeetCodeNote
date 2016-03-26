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

```cpp
class Solution {
public:
    vector<int> grayCode(int n) {
        if(n == 0)  return {0};
        vector<int> cur, pre = grayCode(n - 1);
        int bitMask = 1 << (n - 1);
        for(auto g : pre)
            cur.push_back(g);
        for(int i(pre.size() - 1); i >= 0; --i)
            cur.push_back(bitMask | pre[i]);
        return cur;
    }
};
```