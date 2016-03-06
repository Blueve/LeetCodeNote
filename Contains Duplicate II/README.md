Contains Duplicate II
==========

## C++


```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int, int> hash;
        int N(nums.size());
        for(int i(0); i < N; ++i)
        {
            if(hash.count(nums[i]) && i - hash[nums[i]] <= k)
                return true;
            hash[nums[i]] = i;
        }
        return false;
    }
};
```
