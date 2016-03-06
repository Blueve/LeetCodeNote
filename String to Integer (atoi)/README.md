String to Integer (atoi)
==========

## C++

Using 64bit int to avoid overflow
```cpp
class Solution {
public:
    int myAtoi(string str) {
        int i(0), l(str.size()), symbol(1);
        long long result(0);
        // Skip front space
        while(str[i] == ' ') ++i;
        // Check symbol
        if(str[i] == '-') symbol = -1, ++i;
        else if(str[i] == '+') symbol = 1, ++i;
        // Number
        while(i < l && str[i] >= '0' && str[i] <= '9' && result <= INT_MAX)
        {
            result *= 10;
            result += str[i++] - '0';
        }
        result *= symbol;
        // Handle overflow
             if(result > INT_MAX) return INT_MAX;
        else if(result < INT_MIN) return INT_MIN;
        else return result;
    }
};
```

```cpp
class Solution {
public:
    int myAtoi(string str) {
        int i(0), l(str.size()), symbol(1);
        int result(0);
        // Skip front space
        while(str[i] == ' ') ++i;
        // Check symbol
        if(str[i] == '-') symbol = -1, ++i;
        else if(str[i] == '+') symbol = 1, ++i;
        // Number
        while(i < l && str[i] >= '0' && str[i] <= '9')
        {
            if(result > INT_MAX / 10 || (result == INT_MAX / 10 && str[i] > '7'))
                return symbol == 1 ? INT_MAX : INT_MIN;
            result *= 10;
            result += str[i++] - '0';
        }
        return result * symbol;
    }
};
```
