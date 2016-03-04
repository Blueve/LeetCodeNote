Majority Element
==========

## C++


```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int halfN((nums.size() - 1) >> 1);
        unordered_map<int, int> count;
        for(auto num : nums)
        {
            if(count.count(num)) count[num]++;
            else count[num] = 1;
            
            if(count[num] > halfN) return num;
        }
    }
};
```

Better
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int m(nums[0]), count(1);
        for(auto num : nums)
        {
            if     (num == m) ++count;
            else if(num != m) --count;
            else if(!count)
            {
                m = num;
                count = 1;
            }
        }
        return m;
    }
};
```
