Distinct Subsequences
==========

## C++


```cpp
class Solution {
public:
    int numDistinct(string s, string t) {
        int slen(s.length()), tlen(t.length());
        vector<vector<int>> DP(tlen + 1, vector<int>(slen + 1));
        for(int i(0); i < slen; ++i)
            DP[0][i] = 1;
        for(int i(0); i < tlen; ++i)
        {
            for(int j(0); j < slen; ++j)
            {
                if(t[i] == s[j])
                    DP[i + 1][j + 1] = DP[i][j] + DP[i + 1][j];
                else
                    DP[i + 1][j + 1] = DP[i + 1][j];
            }
        }
        return DP[tlen][slen];
    }
};
```
