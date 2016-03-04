Remove Duplicates from Sorted Array
==========

## C++


```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int index(1), N(nums.size());
        if(!N) return 0;
        
        for(int i(1); i < N; ++i)
        {
            if(nums[i] != nums[i - 1])
                nums[index++] = nums[i];
        }
        return index;
    }
};
```
