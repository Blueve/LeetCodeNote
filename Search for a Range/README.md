Search for a Range
==========

## C++

Two binary search
```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> result(2);
        result[0] = result[1] = -1;
        
        int l(0), r(nums.size()), m;
        while(l < r)
        {
            m = l + (r - l >> 1);
            if(nums[m] < target) l = m + 1;
            else r = m;
        }
        if(target != nums[l]) return result;
        result[0] = l;
        ++target;
        r = nums.size();
        while(l < r)
        {
            m = l + (r - l >> 1);
            if(nums[m] < target) l = m + 1;
            else r = m;
        }
        result[1] = l - 1;
        return result;
    }
};
```
