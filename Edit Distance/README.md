Edit Distance
==========

## C++


```cpp
class Solution {
public:
    int minDistance(string word1, string word2) {
        int l1 = word1.length(), l2 = word2.length();
        vector<vector<int>> DP(l1 + 1, vector<int>(l2 + 1, 0));
        for(int j(0); j <= l2; ++j)
            DP[0][j] = j;
        for(int i(0); i < l1; ++i)
        {
            DP[i + 1][0] = i + 1;
            for(int j(0); j < l2; ++j)
            {
                if(word1[i] == word2[j])
                    DP[i + 1][j + 1] = DP[i][j];
                else
                    DP[i + 1][j + 1] = 1 + min(DP[i][j], min(DP[i][j + 1], DP[i + 1][j]));
            }
        }
        return DP[l1][l2];
    }
};
```
