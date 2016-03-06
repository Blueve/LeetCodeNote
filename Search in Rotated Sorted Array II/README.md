Search in Rotated Sorted Array II
==========

## C++


```cpp
class Solution {
public:
    bool search(vector<int>& nums, int target) {
        int N(nums.size() - 1), l(0), r(N), m(0);
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if(target == nums[m]) return true;
            
            if(nums[m] > nums[l]) // mid on the left
            {
                if(target < nums[l] || target > nums[m])
                    l = m + 1;
                else
                    r = m - 1;
            }
            else if(nums[m] < nums[l]) // mid on the right
            {
                if(target > nums[r] || target < nums[m])
                    r = m - 1;
                else
                    l = m + 1;
            }
            else ++l; // mid on the edge (nums[l] == nums[r])
        }
        return false;
    }
};
```

```cpp
class Solution {
public:
    bool search(vector<int>& nums, int target) {
        int N(nums.size() - 1), l(0), r(N), m(0);
        while(l <= r)
        {
            m = l + (r - l >> 1);
            
            if(target == nums[m]) return true;
            
            if(nums[l] == nums[r])
            {
                --r; continue;
            }
            
            if(nums[m] >= nums[l] && (target < nums[l] || target > nums[m]) ||
               nums[m] <= nums[r] && (target < nums[r] && target < nums[m]))
                l = m + 1;
            else
                r = m - 1;
        }
        return false;
    }
};
```
