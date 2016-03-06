Longest Increasing Subsequence
==========

## C++

O(N^2) Time
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int N(nums.size()), m(1);
        if(!N) return 0;
        vector<int> DP(N, 1);
        // DPi = max(DPi, DPj+1) where j < i && numj < numi
        for(int i(1); i < N; ++i)
        {
            for(int j(0); j < i; ++j)
            {
                if(nums[j] < nums[i])
                    DP[i] = max(DP[i], DP[j] + 1);
            }
            if(DP[i] > m) m = DP[i];
        }
        return m;
    }
};
```
O(Nlog(N)) Time
```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if(nums.empty()) return 0;
        vector<int> sub(1, nums[0]);
        int l, r, m;
        for(auto i : nums)
        {
            if(sub.back() < i) sub.push_back(i);
            else
            {
                // Find a index which just nums[index] >= i
                // and index should as small as possible
                l = 0; r = sub.size();
                while(l < r)
                {
                    m = l + ((r - l) >> 1);
                    if     (i > sub[m]) l = m + 1;
                    else if(i < sub[m]) r = m;
                    else
                    {
                        r = m;
                        break;
                    }
                }
                sub[r] = i;
            }
        }
        return sub.size();
    }
};
```
