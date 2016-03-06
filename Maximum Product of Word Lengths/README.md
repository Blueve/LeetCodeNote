Maximum Product of Word Lengths
==========

## C++


```cpp
class Solution {
public:
    int maxProduct(vector<string>& words) {
        int N(words.size()), max(0), tmp;
        
        vector<int> bitMask(N, 0);
        for(int i(0); i < N; ++i)
        {
            for(auto ch : words[i])
            {
                bitMask[i] |= 1 << (ch - 'a');
            }
            for(int j(i - 1); j >= 0; --j)
            {
                if(!(bitMask[i] & bitMask[j]))
                {
                    tmp = words[i].length() * words[j].length();
                    if(tmp > max) max = tmp;
                }
            }
        }
        return max;
    }
};
```
