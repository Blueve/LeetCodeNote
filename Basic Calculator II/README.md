Basic Calculator II
==========

## C++


```cpp
class Solution {
public:
    int calculate(string s) {
        int len(s.size()), num(0), result(0), cur(0);
        char op('+');
        for(int i(0); i < len; )
        {
            if(s[i] == ' ') ++i;
            else if('0' <= s[i] && s[i] <= '9')
            {
                num = s[i] -'0';
                while(++i < len && '0' <= s[i] && s[i] <= '9')
                {
                    num *= 10;
                    num += s[i] - '0';
                }
                switch(op)
                {
                    case '+' : cur += num; break;
                    case '-' : cur -= num; break;
                    case '*' : cur *= num; break;
                    case '/' : cur /= num; break;
                }
            }
            else
            {
                op = s[i++];
                if(op == '+' || op == '-')
                {
                    result += cur;
                    cur = 0;   
                }
            }
        }
        return result + cur;
    }
};
```
