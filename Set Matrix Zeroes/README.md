Set Matrix Zeroes
==========

## C++


```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int m(matrix.size()), n(matrix[0].size());
        int f(1);
        for(int i(0); i < m; ++i)
        {
            if(matrix[i][0] == 0) f = 0;
            for(int j(1); j < n; ++j)
                if(matrix[i][j] == 0)
                    matrix[0][j] = matrix[i][0] = 0;
        }
        for(int i(1); i < n; ++i)
            if(matrix[0][i] == 0)
                for(int j(1); j < m; ++j) matrix[j][i] = 0;

        for(int i(0); i < m; ++i)
            if(matrix[i][0] == 0)
                for(int j(1); j < n; ++j) matrix[i][j] = 0;

        if(!f) 
            for(int i(0); i < m; ++i) matrix[i][0] = 0;
    }
};
```
