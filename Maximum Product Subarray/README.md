Maximum Product Subarray
==========

## C++


```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int N(nums.size());
        if(!N) return 0;
        
        int maxP, minP, m;
        m = maxP = minP = nums[0];
        for(int i(1); i < N; ++i)
        {
            if(nums[i] >= 0)
            {
                maxP = max(maxP * nums[i], nums[i]);
                minP = min(minP * nums[i], nums[i]);
            }
            else
            {
                int preMaxP = maxP;
                maxP = max(minP * nums[i], nums[i]);
                minP = min(preMaxP * nums[i], nums[i]);
            }
            if(maxP > m) m = maxP;
        }
        return m;
    }
};
```
