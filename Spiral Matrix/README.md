Spiral Matrix
==========

## C++

```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> m(n, vector<int>(n, 0));
        int count(1), N(n * n);
        int top(0), bottom(n - 1), left(0), right(n - 1);
        while(count <= N)
        {
            for(int i(left); i <= right; ++i)
                m[top][i] = count++;
            ++top;
            
            for(int i(top); i <= bottom; ++i)
                m[i][right] = count++;
            --right;
                
            for(int i(right); i >= left; --i)
                m[bottom][i] = count++;
            --bottom;
                
            for(int i(bottom); i >= top; --i)
                m[i][left] = count++;
            ++left;
        }
        return m;
    }
};
```
