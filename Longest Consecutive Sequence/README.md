Longest Consecutive Sequence
==========

## C++


```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_map<int, int> s;
        int m = INT_MIN, tmp;
        for(auto i : nums)
        {
            if(s.count(i)) continue;
            s[i] = 0;
            if(s.count(i + 1)) // i -> i + 1
            {
                tmp = s[i] = s[i + 1 + s[i + 1]] = s[i + 1] + 1;
            }
            if(s.count(i - 1)) // i - 1 -> i
            {
                tmp = s[i + s[i]] = s[i - 1 - s[i - 1]] += s[i] + 1;
            }
            if(tmp > m) m = tmp;
        }
        return m + 1;
    }
};
```
Better
```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_map<int, int> s;
        int m = 0, tmp;
        for(auto i : nums)
        {
            if(s[i]) continue;
            // leftCount + 1 + rightCount
            tmp = s[i + 1] + s[i - 1] + 1;
            // left = right = tmp
            s[i] = s[i + s[i + 1]] = s[i - s[i - 1]] = tmp;
            
            if(tmp > m) m = tmp;
        }
        return m;
    }
};
```