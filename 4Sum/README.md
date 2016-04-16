4Sum
==========

## C++

O(N^3)
```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>> result;
        sort(nums.begin(), nums.end());
        int n = nums.size();
        for(int i(0); i < n - 3; ++i)
        {
            for(int j(i + 1); j < n - 2; ++j)
            {
                int t = target - (nums[i] + nums[j]);
                
                // Black magic
                // Need increase 'i' to reduce t
                if(nums[j + 1] + nums[j + 2] > t) break;
                // Need increase 'j' to reduce t
                if(nums[n - 1] + nums[n - 2] < t) continue;
                
                int l = j + 1, r = n - 1;
                while(l < r)
                {
                    int sum = nums[l] + nums[r];
                    
                    if(t > sum)
                        ++l;
                    else if(t < sum)
                        --r;
                    else
                    {
                        int a = nums[i], b = nums[j], c = nums[l], d = nums[r];
                        result.push_back({a, b, c, d});
                        while(l < r && nums[l] == c) ++l;
                        while(l < r && nums[r] == d) --r;
                    }
                }
                while (j + 1 < n && nums[j + 1] == nums[j])
                    ++j;
            }
            while (i + 1 < n && nums[i + 1] == nums[i])
                ++i;
        }
        return result;
    }
};
```
