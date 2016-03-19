Search in Rotated Sorted Array
==========

## C++


```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l(0), r(nums.size() - 1), m(0);
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if(nums[m] == target) return m;
            else if(nums[m] >= nums[l])
            {
                if(target < nums[l] || target > nums[m])
                    l = m + 1;
                else
                    r = m - 1;
            }
            else
            {
                if(target > nums[r] || target < nums[m])
                    r = m - 1;
                else
                    l = m + 1;
            }
        }
        return -1;
    }
};
```

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l(0), r(nums.size() - 1), m(0);
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if(nums[m] == target) return m;
            
            if(nums[m] >= nums[l] && (target < nums[l] || target > nums[m]) ||
               nums[m] <= nums[r] && target < nums[l] && target > nums[m])
                l = m + 1;
            else
                r = m - 1;
        }
        return -1;
    }
};
```
