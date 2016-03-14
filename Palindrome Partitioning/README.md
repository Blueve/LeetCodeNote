Palindrome Partitioning
==========

## C++


```cpp
class Solution {
public:
    vector<vector<string>> partition(string s) {
        // substr + partition(substr->end)
        vector<vector<string>> result;
        vector<string> part;
        _partition(s, 0, result, part);
        return result;
    }
    
    void _partition(string& s, int start, vector<vector<string>>& result, vector<string>& part)
    {
        int len = s.size();
        if(start == len)
        {
            result.push_back(part);
            return;
        }
        
        // Find prefix
		for (int i(start); i < len; ++i)
		{
			// Check palindrome
			int l, r;
			for (l = start, r = i; l < r; l++, r--)
			{
				if (s[l] != s[r]) break;
			}
			if (l < r) continue;

			// Generate
			part.push_back(s.substr(start, i + 1 - start));
			_partition(s, i + 1, result, part);
			part.pop_back();
		}
    }
};
```
