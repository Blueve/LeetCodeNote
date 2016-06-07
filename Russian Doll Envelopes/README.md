Russian Doll Envelopes
==========

## C++


O(N^2) Time, O(N) Space
```cpp
class Solution {
    
    inline
    bool canFitInto(const pair<int, int>& lhs, const pair<int, int>& rhs) {
        return lhs.first < rhs.first && lhs.second < rhs.second;
    }
    
public:
    int maxEnvelopes(vector<pair<int, int>>& envelopes) {
        if(envelopes.empty()) return 0;
        
        sort(envelopes.begin(), envelopes.end(),
            [](const pair<int, int>& lhs, const pair<int, int>& rhs) {
                return lhs.first == rhs.first ? lhs.second < rhs.second : lhs.first < rhs.first;
            });
        
        auto n = envelopes.size();
        int result;
        vector<int> DP(n);
        result = DP[n - 1] = 1;
        for(int i = n - 2; i >= 0; --i)
        {
            int max = 0;
            for(int j = n - 1; j > i; --j)
            {
                if(canFitInto(envelopes[i], envelopes[j]) && DP[j] > max)
                    max = DP[j];
            }
            DP[i] = max + 1;
            if(DP[i] > result) result = DP[i];
        }
        return result;
    }
};
```

O(NlogN) Time, O(N) Space
```cpp
class Solution {
public:
    int maxEnvelopes(vector<pair<int, int>>& envelopes) {
        sort(envelopes.begin(), envelopes.end());
        
        int i = 0, n = envelopes.size();
        vector<int> result;
        result.reserve(n);
        while(i < n)
        {
            deque<vector<int>::iterator> q;
            int cur = envelopes[i].first;
            while(i < n && envelopes[i].first == cur)
            {
                q.push_front(lower_bound(result.begin(), result.end(), envelopes[i++].second));
            }
            
            for(int j = 0; j < q.size(); ++j)
            {
                if(q[j] == result.end())
                    result.push_back(envelopes[i - j - 1].second);
                else
                    *(q[j]) = envelopes[i - j - 1].second;
            }
        }
        
        return result.size();
    }
};
```
