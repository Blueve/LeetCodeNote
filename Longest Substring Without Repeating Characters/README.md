Longest Substring Without Repeating Characters
==========

## C++


```cpp
class Solution {
public:
	int lengthOfLongestSubstring(string s) {
		int start(-1), m(0), len = s.length();
		vector<int> cIndex(128, -1);
		for(int i(0); i < len; ++i)
		{
		    // If meet before, record new start position
		    if(cIndex[s[i]] > start)
		        start = cIndex[s[i]];
		    cIndex[s[i]] = i;
		    // Compare between the left part and cur
		    m = max(m, i - start);
		}
		return m;
	}
};
```
