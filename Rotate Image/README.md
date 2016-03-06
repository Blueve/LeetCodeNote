Rotate Image
==========

## C++


```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n(matrix.size());
        
        for(auto& line : matrix)
            reverse(line.begin(), line.end());
            
        for(int i(0); i < n - 1; ++i)
            for(int j(0); j < n - 1 - i; ++j)
                swap(matrix[i][j], matrix[n - j - 1][n - i - 1]);
    }
};
```
