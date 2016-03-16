Ugly Number II
==========

## C++


```cpp
class Solution {
public:
    int nthUglyNumber(int n) {
        int p[] = {2, 3, 5};
        vector<int> ugly(n, INT_MAX), index(3, 0);
        ugly[0] = 1;
        for(int i(1); i < n; ++i)
        {
            for(int j(0); j < 3; ++j)
            {
                ugly[i] = min(ugly[i], ugly[index[j]] * p[j]);
            }
            
            for(int j(0); j < 3; ++j)
            {
                if(ugly[i] == ugly[index[j]] * p[j])
                {
                    ++index[j];
                }
            }
        }
        return ugly.back();
    }
};
```
Better
```cpp
class Solution {
public:
    int nthUglyNumber(int n) {
        int p[] = {2, 3, 5};
        vector<int> ugly(n, INT_MAX), index(3, 0);
        ugly[0] = 1;
        for(int i(1); i < n; ++i)
        {
            ugly[i] = min(ugly[index[0]] * 2, min(ugly[index[1]] * 3, ugly[index[2]] * 5));
            
            if(ugly[i] == ugly[index[0]] * p[0]) ++index[0];
            if(ugly[i] == ugly[index[1]] * p[1]) ++index[1];
            if(ugly[i] == ugly[index[2]] * p[2]) ++index[2];
        }
        return ugly.back();
    }
};
```
