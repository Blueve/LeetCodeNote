Move Zeroes
==========

## C++


```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int p(0), i, N(nums.size());
        // Find first zero
        while(p < N && nums[p] && ++p);
        // Swap
        for(i = p + 1; i < N; ++i)
        {
            if(nums[i])
            {
                nums[p++] = nums[i];
                nums[i] = 0;
            }
        }
    }
};
```
