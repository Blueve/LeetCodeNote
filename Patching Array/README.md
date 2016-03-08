Patching Array
==========

## C++


```cpp
class Solution {
public:
    int minPatches(vector<int>& nums, int n) {
        long long sum(1);
        int patches(0), i(0), N(nums.size());
        while(sum <= n)
        {
            // Try test if sum missed
            if(i < N && nums[i] <= sum)
            {
                // We can build 1 -> sum + num[i] if num[i] <= sum
                sum += nums[i++];
            }
            // If nums[i] > sum,
            // means there is a number should be patch
            else
            {
                // Patch 'sum' then we can build 1 -> sum + sum
                sum <<= 1; // sum *= 2;
                ++patches;
            }
        }
        return patches;
    }
};
```
