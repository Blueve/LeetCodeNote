Product of Array Except Self
==========

## C++


```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int N(nums.size());
        vector<int> result(N, 1);
        for(int i(1); i < N; ++i)
        {
            result[i] *= result[i - 1] * nums[i - 1];
        }
        int suffix(1);
        for(int i(N - 1); i >= 0; --i)
        {
            result[i] *= suffix;
            suffix *= nums[i];
        }
        return result;
    }
};
```
