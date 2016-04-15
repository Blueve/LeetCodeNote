Additive Number
==========

## C++


```cpp
class Solution {
public:
    bool isAdditiveNumber(string num) {
        int len = num.length() - 1;
        for(int i(1); i < len; ++i)
        {
            for(int j(0); j < i; ++j)
            {
                // num1 : [0, j]
                // num2 : [j + 1, i]
                if(verify(num, j + 1, i + 1))
                    return true;
            }
        }
        return false;
    }
    
    bool verify(string& num, int n1, int n2)
    {
        if(num[0] == '0' && n1 > 1 ||
           num[n1] == '0' && n2 - n1 > 1) return false;
        
        int len = num.length(), p(n2);
        // [0, n1) [n1, n2)
        string num1 = num.substr(0, n1);
        string num2 = num.substr(n1, n2 - n1);
        string sum = add(num1, num2);
        
        if(p + sum.length() > len) return false;
        while(p + sum.length() <= len)
        {
            for(int i(0), j(p); i < sum.length(); ++i, ++j)
                if(sum[i] != num[j]) return false;
            num1 = num2;
            num2 = sum;
            p += sum.length();
            sum = add(sum, num1);
        }
        return true;
    }
    
    string add(string a, string b)
    {
        int l1 = a.length(), l2 = b.length();
        if(l1 < l2) return add(b, a);
        
        reverse(a.begin(), a.end());
        reverse(b.begin(), b.end());
        
        a.push_back('0');
        for(int i(0); i < l2; ++i)
        {
            a[i] += b[i] - '0';
            if(a[i] >= 10 + '0')
            {
                a[i] -= 10;
                a[i + 1]++;
            }
        }
        for(int i(l2); i < l1; ++i)
        {
            if(a[i] >= 10 + '0')
            {
                a[i] -= 10;
                a[i + 1]++;
            }
            else break;
        }
        if(a.back() == '0') a.pop_back();
        reverse(a.begin(), a.end());
        return a;
    }
};
```
