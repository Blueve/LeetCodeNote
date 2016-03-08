Letter Combinations of a Phone Number
==========

## C++


```cpp
class Solution {
    string mapping[8] = {"abc", "def", "ghi", "jkl", "nmo", "pqrs", "tuv", "wxyz"};
public:
    vector<string> letterCombinations(string digits) {
        vector<string> result, sub;
        if(digits.size() > 1)
            sub = letterCombinations(digits.substr(1));
        else if(digits.size() == 1)
            sub = {""};
        else
            return result;
            
        for(auto c : mapping[digits[0] - '2'])
            for(auto& s : sub)
                result.push_back(c + s);
                
        return result;
    }
};
```
