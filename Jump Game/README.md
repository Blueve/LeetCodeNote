Jump Game
==========

## C++


```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int N(nums.size());
        vector<bool> DP(N, false);
        DP[0] = true;
        for(int i(1); i < N; ++i)
        {
            for(int j(i - 1); j >= 0; --j)
            {
                if(DP[j] && nums[j] + j >= i)
                {
                    DP[i] = true;
                    break;
                }
            }
        }
        return DP[N - 1];
    }
};
```
Better, o(1), O(N)
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int N(nums.size()), i, m(0);
        for(i = 0; i < N && i <= m; ++i)
        {
            m = max(m, i + nums[i]);
            if(m >= N - 1) return true;
        }
        return false;
    }
};
```
Better for worst case, o(N), O(N)
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int N(nums.size()), i, m(0);
        for(i = 0; i < N && i <= m; ++i)
        {
            m = max(m, i + nums[i]);
        }
        return i == N;
    }
};
```