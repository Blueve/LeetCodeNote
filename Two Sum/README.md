Two Sum
==========

## C++

O(N^2)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int N(nums.size());
        for(int i(0); i < N; ++i)
        {
            for(int j(i + 1); j < N; ++j)
            {
                if(nums[i] + nums[j] == target)
                    return {i, j};
            }
        }
    }
};
```
O(N)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int N(nums.size());
        unordered_map<int, int> hash;
        for(int i(0); i < N; ++i)
        {
            int t = target - nums[i];
            if(hash.count(t))
                return {hash[t], i};
            hash[nums[i]] = i;
        }
    }
};
```
