Summary Ranges
==========

## C++


```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> result;
        int N(nums.size());
        if(!N) return result;
        long from(nums[0]), to(from);
        for(auto i : nums)
        {
            if(i - to > 1)
            {
                if(from == to)
                    result.push_back(to_string(from));
                else
                    result.push_back(to_string(from) + "->" + to_string(to));
                from = i;
            }
            to = i;
        }
        if(from == to)
            result.push_back(to_string(from));
        else
            result.push_back(to_string(from) + "->" + to_string(to));
        return result;
    }
};
```
