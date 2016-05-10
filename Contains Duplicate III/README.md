Contains Duplicate III
==========

## C++

O(NlogK)
```cpp
class Solution {
public:
    bool containsNearbyAlmostDuplicate(vector<int>& nums, int k, int t) {
        set<int> ordered;
        for(int i(0); i < nums.size(); ++i)
        {
            // Keep ordered's elem number at most k
            if(i > k) ordered.erase(nums[i - k - 1]);
            
            // Find a number in ordered, and make sure 
            // [*p >= nums[i] - t] => [*p - nums[i] >= -t]
            auto p = ordered.lower_bound(nums[i] - t);
            if(p != ordered.end() && *p - nums[i] <= t)
                return true;
            
            ordered.insert(nums[i]);
        }
        return false;
    }
};
```
