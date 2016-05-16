Remove Duplicate Letters
==========

## C++


```cpp
class Solution {
public:
    string removeDuplicateLetters(string s) {
        if(s.empty()) return "";
        
        vector<int> count(26), tmp;
        for(auto ch : s)
            ++count[ch - 'a'];
        
        string result;
        while(!s.empty())
        {
            // Find the first char which are as smaller as possible
            // and keep the string still have all char
            int len = s.length(), p(0);
            tmp = count;
            for(int i(0); i < len; ++i)
            {
                if(s[i] < s[p])
                {
                    p = i;
                    tmp = count;
                }
                if(--count[s[i] - 'a'] == 0)
                    break;
            }
            swap(count, tmp);
            char r = s[p];
            
            // Reuslt have this char
            result.push_back(r);
            
            // Remove all char which equals this char appeared after
            int i, j;
            for(i = 0, j = p + 1; j < len;)
            {
                if(s[j] != r)
                    s[i++] = s[j++];
                else
                    ++j;
            }
            s.resize(i);
        }
        return result;
    }
};
```

Better
```cpp
class Solution {
public:
    string removeDuplicateLetters(string s) {
        vector<int> count(128);
        vector<bool> visit(128);
        
        for(auto ch : s)
            ++count[ch];
        
        string result;
        result += 'a' - 1;
        for(auto ch : s)
        {
            --count[ch];
            if(visit[ch]) continue;
            while(ch < result.back() && count[result.back()])
            {
                visit[result.back()] = false;
                result.pop_back();
            }
            result.push_back(ch);
            visit[ch] = true;
        }
        return result.substr(1);
    }
};
```
