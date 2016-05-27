Palindrome Partitioning II
==========

## C++

O(N^2) Time, O(N^2) Space
```cpp
class Solution {
public:
    int minCut(string s) {
        if(s.empty()) return 0;
        int len = s.length();
        vector<vector<bool>> isPalindrome(len, vector<bool>(len));
        vector<int> DP(len);
        
        for(int i = 0; i < len; ++i)
        {
            DP[i] = i;
            for(int j = 0; j <= i; ++j)
            {
                // If isP[j + 1][i - 1] == true && s[i] == s[j]
                // then s[j->i] isP
                if(s[i] == s[j] && (i - j < 2 || isPalindrome[j + 1][i - 1]))
                {
                    isPalindrome[j][i] = true;
                    DP[i] = j ? min(DP[i], DP[j - 1] + 1) : 0;
                }
            }
        }
        return DP.back();
    }
};
```
