Search Insert Position
==========

## C++


```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int l(0), r(nums.size() - 1), m;
        
        while(l <= r)
        {
            m = (r - l) / 2 + l;
            if(target > nums[m]) l = m + 1;
            else if(target < nums[m]) r = m - 1;
            else return m;
        }
        return l;
    }
};
```
