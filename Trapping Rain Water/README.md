Trapping Rain Water
==========

## C++


```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int left(0), right(height.size() - 1), l(0), r(0), sum(0);
        
        while(left <= right)
        {
            if(height[left] < height[right])
            {
                if(height[left] > l)
                    l = height[left];
                else
                    sum += l - height[left];
                ++left;
            }
            else
            {
                if(height[right] > r)
                    r = height[right];
                else
                    sum += r - height[right];
                --right;
            }
        }
        return sum;
    }
};
```
