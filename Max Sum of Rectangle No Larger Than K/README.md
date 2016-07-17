Max Sum of Rectangle No Larger Than K
==========

## C++


```cpp
class Solution {
public:
    int maxSumSubmatrix(vector<vector<int>>& matrix, int k) {
        if(matrix.empty()) return 0;
        
        int n = matrix.size();
        int m = matrix[0].size();
        
        bool flag = n > m;
        if(flag) swap(n, m);
        
        int maxSum = INT_MIN;
        for(int i = 0; i < n; ++i)
        {
            vector<int> sum(m);
            for(int l = i; l < n; ++l)
            {
                // Compute current sum arr
                for(int p = 0; p < m; ++p)
                {
                    sum[p] += flag ? matrix[p][l] : matrix[l][p];
                }
            
                // Find max subarr
                set<int> accumulate;
                accumulate.insert(0);
                int cur = 0;
                for(int s : sum)
                {
                    cur += s;
                    auto it = accumulate.lower_bound(cur - k);
                    if(it != accumulate.end())
                        maxSum = max(maxSum, cur - *it);
                    accumulate.insert(cur);
                }
            }
        }
        return maxSum;
    }
};
```
