Integer to Roman
==========

## C++


```cpp
class Solution {
public:
    const char cTable[8] = "MDCLXVI";
    const int nTable[7] = {1000, 500, 100, 50, 10, 5, 1};
    
    string intToRoman(int num) {
        string result;
        int p(0), tmp;
        while(num)
        {
            tmp = num / nTable[p];
            if(tmp == 9)
            {
                result += cTable[p];
                result += cTable[p - 2];
            }
            else if(tmp > 5)
            {
                result += cTable[p - 1];
                result += string(tmp - 5, cTable[p]);
            }
            else if(tmp == 5)
            {
                result += cTable[p - 1];
            }
            else if(tmp == 4)
            {
                result += cTable[p];
                result += cTable[p - 1];
            }
            else if(tmp)
            {
                result += string(tmp, cTable[p]);
            }
            num -= tmp * nTable[p];
            p += 2;
        }
        return result;
    }
};
```
Better
```cpp
class Solution {
public:
    const string rTable[13] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    const int nTable[13] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
    
    string intToRoman(int num) {
        string result;
        int p(0), tmp;
        while(num)
        {
            for(int i(0); i < 13; ++i)
            {
                if(num >= nTable[i])
                {
                    num -= nTable[i];
                    result += rTable[i];
                    break;
                }
            }
        }
        return result;
    }
};
```
Better O(1) Time
```cpp
class Solution {
public:
    const string M[4] = {"", "M", "MM", "MMM"};
    const string C[10] = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
    const string X[10] = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
    const string I[10] = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};

    string intToRoman(int num) {
        return M[num/1000] + C[(num%1000)/100] + X[(num%100)/10] + I[num%10];
    }
};
```
