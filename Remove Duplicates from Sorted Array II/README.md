Remove Duplicates from Sorted Array II
==========

## C++


```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int N(nums.size());
        if(!N) return 0;
        
        int p(1), count(1), pre(nums[0]);
        for(int i(1); i < N; ++i)
        {
            nums[p++] = nums[i];
            if(nums[i] == pre)
            {
                if(++count > 2) p--;
            }
            else count = 1;
            pre = nums[i];
        }
        return p;
    }
};
```
Better
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int p(0);
        
        for(auto n : nums)
        {
            if(p < 2 || n > nums[p - 2])
                nums[p++] = n;
        }
        return p;
    }
};
```
