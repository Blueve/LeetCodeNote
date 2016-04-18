Remove Invalid Parentheses
==========

## C++


```cpp
class Solution {
public:
    vector<string> removeInvalidParentheses(string s) {
        if(s.empty()) return {""};
        unordered_set<string> hashT;
        vector<string> result;
        queue<string> q;
        q.push(s);
        while(!q.empty())
        {
            int n = q.size();
            while(n--)
            {
                string cur = q.front();
                q.pop();
                
                if(isValid(cur))
                    result.push_back(cur);
                else
                {
                    for(int i(0); i < cur.length(); ++i)
                    {
                        if(cur[i] != '(' && cur[i] != ')')
                            continue;
                        
                        if(i && cur[i] == cur[i - 1])
                            continue;
                            
                        auto next = cur.substr(0, i) + cur.substr(i + 1);
                        if(!hashT.count(next))
                        {
                            q.push(next);
                            hashT.insert(next);
                        }
                    }
                }
            }
            if(!result.empty())
                return result;
        }
        return {""};
    }
    
    bool isValid(string s)
    {
        int cnt = 0;
        for(auto c : s)
        {
            if(c == '(') ++cnt;
            else if(c == ')') --cnt;
            
            if(cnt < 0) return false;
        }
        return !cnt;
    }
};
```
