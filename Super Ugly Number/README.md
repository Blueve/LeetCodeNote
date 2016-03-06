Super Ugly Number
==========

## C++


```cpp
class Solution {
public:
    int nthSuperUglyNumber(int n, vector<int>& primes) {
        int k(primes.size());
        vector<int> ugly(n, INT_MAX), index(k, 0);
        ugly[0] = 1;
        for(int i(1); i < n; ++i)
        {
            for(int j(0); j < k; ++j)
            {
                ugly[i] = min(ugly[i], ugly[index[j]] * primes[j]);
            }
            
            for(int j(0); j < k; ++j)
            {
                if(ugly[i] == ugly[index[j]] * primes[j])
                {
                    ++index[j];
                }
            }
        }
        return ugly.back();
    }
};
```
