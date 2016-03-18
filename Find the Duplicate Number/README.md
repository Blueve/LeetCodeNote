Find the Duplicate Number
==========

## C++


```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int fast(nums[nums[0]]), slow(nums[0]);
        // Meet in cycle
        while(slow != fast)
        {
            slow = nums[slow];
            fast = nums[nums[fast]];
        }
        // Find the start point of cycle
        fast = 0;
        while(slow != fast)
        {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
};
```
