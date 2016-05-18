Largest Rectangle in Histogram
==========

## C++


```cpp
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        heights.push_back(0);
        int n = heights.size();
        
        stack<int> stk;
        int i = 0, m = 0;
        while(i < n)
        {
            // Keep the height of index in stack is asc
            if(stk.empty() || heights[i] >= heights[stk.top()])
                stk.push(i++);
            else
            {
                // If current height lower than stack's top
                // then try to compute it area
                // until height value of stack's top lower than current height
                int h = stk.top();
                stk.pop();
                m = max(m, heights[h] * (stk.empty() ? i : i - stk.top() - 1));
            }
        }
        return m;
    }
};
```
