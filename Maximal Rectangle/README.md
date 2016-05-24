Maximal Rectangle
==========

## C++

Similar with [Largest Rectangle in Histogram]
```cpp
class Solution {
public:
    int maximalRectangle(vector<vector<char>>& matrix) {
        if(matrix.empty()) return 0;
        int n = matrix.size();
        int m = matrix[0].size();
        int max = 0;
        
        vector<int> height(m + 1);
        for(int i(0); i < n; ++i)
        {
            stack<int> stk;
            for(int j(0); j < m + 1; ++j)
            {
                // ->
                // 1 0 ? = 1
                // 1 1 0 = 2
                // 1 1 0 = 2
                // . . .
                if(j < m)
                {
                    if(matrix[i][j] == '1')
                        ++height[j];
                    else
                        height[j] = 0;
                }
                // Base on col no. i, find the max area
                while(!stk.empty() && height[stk.top()] >= height[j])
                {
                    auto h = height[stk.top()];
                    stk.pop();
                    auto w = stk.empty() ? j : j - stk.top() - 1;
                    max = std::max(h * w, max);
                }
                stk.push(j);
            }
        }
        return max;
    }
};
```
