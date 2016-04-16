3Sum
==========

## C++

O(N^2logN)
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        sort(nums.begin(), nums.end());
        
        int a, b, c;
        a = 0, c = nums.size();
        while(c--)
        {
            for(a = 0; a < c; ++a)
            {
                int b = -(nums[a] + nums[c]), l = a + 1, r = c - 1, m;
                while(l <= r)
                {
                    m = l + (r - l >> 1);
                    if(nums[m] > b) r = m - 1;
                    else if(nums[m] < b) l = m + 1;
                    else
                    {
                        result.push_back({nums[a], b, nums[c]});
                        break;
                    }
                }
                while(a < c && nums[a] == nums[a + 1]) ++a;
            }
            while(c > 0 && nums[c] == nums[c - 1]) --c;
        }
        return result;
    }
};
```

O(N^2)
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        sort(nums.begin(), nums.end());
        for(int i(0); i < nums.size(); ++i)
        {
            int target = -nums[i];
            int l = i + 1, r = nums.size() - 1;
            while(l < r)
            {
                int sum = nums[l] + nums[r];
                
                if(target > sum)
                    ++l;
                else if(target < sum)
                    --r;
                else
                {
                    int a = nums[i], b = nums[l], c = nums[r];
                    result.push_back({a, b, c});
                    while(l < r && nums[l] == b) ++l;
                    while(l < r && nums[r] == c) --r;
                }
            }
            while (i + 1 < nums.size() && nums[i + 1] == nums[i])
                ++i;
        }
        return result;
    }
};
```
