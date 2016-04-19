Jump Game II
==========

## C++


```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int N = nums.size(), cur(0);
        vector<int> DP(N);
        if(nums.size() < 2) return 0;
        for(int i(0); i < N; ++i)
        {
            int next = i + nums[i];
            if(next > cur)
            {
                if(next >= N - 1) return DP[i] + 1;
                cur = next;
            }
            for(int j(cur); j > 0 && !DP[j]; --j)
                DP[j] = DP[i] + 1;
        }
        return DP[N - 1];
    }
};
```
