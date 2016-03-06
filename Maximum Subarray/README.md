Maximum Subarray
==========

## C++


```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int sum(0), m(nums[0]);
        for(auto num : nums)
        {
            if(sum < 0) sum = num;
            else sum += num;
            
            if(sum > m) m = sum;
        }
        return m;
    }
};
```
