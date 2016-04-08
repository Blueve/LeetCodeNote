Basic Calculator
==========

## C++


```cpp
class Solution {
public:
    int calculate(string s) {
        
        // Prepare for calculate
        stack<int> numbers;
        stack<char> ops;
        bool hasNumber(false);
        int num = 0, l, r;
        // Handle tail
        ops.push('(');
        s += ')';
        for(auto c : s)
        {
            if(isdigit(c))
            {
                hasNumber = true;
                num *= 10;
                num += c - '0';
            }
            else if(c != ' ')
            {
                if(hasNumber)
                {
                    numbers.push(num);
                    num = 0;
                    hasNumber = false;
                }
                if(c == '+' || c == '-')
                {
                    if(ops.top() != '(')
                    {
                        r = numbers.top(); numbers.pop();
                        l = numbers.top(); numbers.pop();
                        numbers.push(calop(l, r, ops.top()));
                        ops.pop();
                    }
                    ops.push(c);
                }
                else if(c == '(') ops.push('(');
                else if(c == ')')
                {
                    r = numbers.top(); numbers.pop();
                    if(ops.top() == '(')
                        numbers.push(r);
                    else
                    {
                        l = numbers.top(); numbers.pop();
                        numbers.push(calop(l, r, ops.top()));
                        ops.pop();
                    }
                    ops.pop();
                }
            }
        }
        return numbers.top();
    }
    
    int calop(int l, int r, char op)
    {
        return (op == '+' ? l + r : l - r);
    }
};
```
