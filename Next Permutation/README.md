Next Permutation
==========

## C++


```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        // From right to left, find first n[i] < n[i + 1],
        // named n[i] 'replace number'/ i 'replace place'
        // From right to left, find first n[j] > n[i]
        // Swap n[i] n[j]
        // Reverse i + 1 to end
        int N(nums.size());
        for(int i(N - 2); i >= 0; --i)
        {
            if(nums[i] < nums[i + 1])
            {
                int r = N - 1;
                while(nums[r] <= nums[i]) --r;
                swap(nums[i], nums[r]);
                reverse(nums.begin() + i + 1, nums.end());
                return;
            }
        }
        reverse(nums.begin(), nums.end());
    }
};
```
