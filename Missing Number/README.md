Missing Number
==========

## C++


```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int N(nums.size()), sum(0);
        int total = N * (N + 1) >> 1;
        
        for(auto num : nums) sum += num;
        return total - sum;
    }
};
```
Better - wont't overflow
```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int result(nums.size()), N(result);
        for(int i(0); i < N; ++i)
        {
            result ^= nums[i];
            result ^= i;
        }
        return result;
    }
};
```
