Maximal Square
==========

## C++

Search and expend
```cpp
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        int max = 1;
        int n = matrix.size();
        if(!n) return 0;
        int m = matrix[0].size();
        for(int i(0); i < n; ++i)
        {
            for(int j(0); j < m; ++j)
            {
                if(matrix[i][j] == '0')
                    continue;
                int nn = i + max;
                int mm = j + max;
                bool valid = true;
                
                if(mm > m) break;
                if(nn > n) return (max - 1) * (max - 1);
                
                // Confirm current square
                for(int x(i); x < nn; ++x)
                {
                    for(int y(j); y < mm; ++y)
                    {
                        if(matrix[x][y] == '0')
                        {
                            valid = false;
                            goto CONFIRMED;
                        }
                    }
                }
                CONFIRMED:
                if(!valid) continue;
                
                // Try expend
                while(valid)
                {
                    ++nn, ++mm, ++max;
                    if(nn > n || mm > m)
                        break;
                    for(int k(0); k < max; ++k)
                    {
                        if(matrix[i + max - 1][j + k] == '0' ||
                           matrix[i + k][j + max - 1] == '0')
                        {
                            valid = false;
                            break;
                        }
                    }
                }
            }
        }
        return (max - 1) * (max - 1);
    }
};
```

Better, DP
```cpp
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        int n = matrix.size();
        if(!n) return 0;
        int m = matrix[0].size();
        
        vector<int> DP(n + 1);
        int max = 0, pre = 0;
        for(int j(0); j < m; ++j)
        {
            for(int i(1); i <= n; ++i)
            {
                int tmp = DP[i];
                if(matrix[i - 1][j] == '0')
                    DP[i] = 0;
                else
                {
                    DP[i] = min(DP[i], min(DP[i - 1], pre)) + 1;
                    if(DP[i] > max) max = DP[i];
                }
                pre = tmp;
            }
        }
        return max * max;
    }
};
```
