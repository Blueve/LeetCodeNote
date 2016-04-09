Minimum Size Subarray Sum
==========

## C++


```cpp
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int left(0), amount(0), minLen(INT_MAX);
        for(int i(0); i < nums.size(); ++i)
        {
            amount += nums[i];
            while(amount >= s)
            {
                minLen = min(minLen, i - left + 1);
                amount -= nums[left++];
            }
        }
        return minLen == INT_MAX ? 0 : minLen;
    }
};
```
