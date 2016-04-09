Restore IP Addresses
==========

## C++


```cpp
class Solution {
public:
    vector<string> restoreIpAddresses(string s) {
        vector<string> result;
        split(result, s, 0, "", 0);
        return result;
    }
    
    void split(vector<string>& result, string& s, int i, string ip, int n)
    {
        if(n == 4)
        {
            if(i == s.length())
                result.push_back(ip.substr(1));
            return;
        }
        
        if(s[i] == '0')
            split(result, s, i + 1, ip + ".0", n + 1);
        else
        {
            for(int l(1); l <= 3 && i + l <= s.length(); ++l)
            {
                string sub = s.substr(i, l);
                if(atoi(sub.c_str()) < 256)
                    split(result, s, i + l, ip + "." + sub, n + 1);
            }
        }
    }
};
```
