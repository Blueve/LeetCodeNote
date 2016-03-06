Remove Element
==========

## C++


```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int N(nums.size());
        for(int i(0); i < N;)
        {
            if(nums[i] == val) nums[i] = nums[--N];
            else ++i;
        }
        return N;
    }
};
```
