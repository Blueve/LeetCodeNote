Largest Number
==========

## C++


```cpp
class Solution {
public:
    string largestNumber(vector<int>& nums) {
        vector<string> s_nums;
        for (auto n : nums)
            s_nums.push_back(to_string(n));
        
        sort(s_nums.begin(), s_nums.end(), [](string& a, string& b) {
            return a + b > b + a;
        });
        
        string result;
        int n = s_nums.size(), i;
        for(i = 0; i < n; ++i)
            if(s_nums[i][0] != '0') break;
        for(;i < n; ++i)
            result += s_nums[i];
        return result.empty() ? "0" : result;
    }
};
```
