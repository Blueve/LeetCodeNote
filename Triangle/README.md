Triangle
==========

## C++


```cpp
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int N(triangle.size());
        
        vector<int> DP(triangle.back());
        for(int i(N - 2); i >= 0; --i)
        {
            for(int j(0); j <= i; ++j)
            {
                DP[j] = triangle[i][j] + min(DP[j], DP[j + 1]);
            }
        }
        return DP[0];
    }
};
```
