Fraction to Recurring Decimal
==========

## C++


```cpp
class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        string decimal;
        decimal = (numerator >= 0 ^ denominator >= 0 &&
                   numerator != 0) ?  "-" : "";
        auto n = abs((long long)numerator);
        auto d = abs((long long)denominator);
        
        decimal += to_string(n / d);
        auto m = n % d;
        
        if(m == 0) return decimal;
        decimal += '.';
        
        unordered_map<int, int> h;
        while(m)
        {
            m *= 10;
            auto item = h.find(m);
            if(item != h.end())
            {
                decimal.insert(item->second, "(");
                return decimal += ')';
            }
            h[m] = decimal.length();
            
            decimal += '0' + m / d;
            m = m % d;
        }
        return decimal;
    }
};
```
