Multiply Strings
==========

## C++


```cpp
class Solution {
public:
    string multiply(string num1, string num2) {
        int l1 = num1.size(), l2 = num2.size();
        int n = l1 + l2 - 1;
        vector<int> mul(l1 + l2);
        for(int i(l1 - 1); i >= 0; --i)
        {
            for(int j(l2 - 1); j >= 0; --j)
            {
                int tmp = (num1[i] - '0') * (num2[j] - '0') + mul[n - i - j - 1];
                mul[n - i - j - 1] = tmp % 10;
                mul[n - i - j] += tmp / 10;
            }
        }
        while(n && !mul[n]) --n;
        
        string result(n + 1, '0');
        for(int i(n), j(0); i >= 0; --i, ++j)
            result[j] += mul[i];
        return result;
    }
};
```
