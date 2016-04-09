Evaluate Reverse Polish Notation
==========

## C++


```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> num;
        int l, r;
        for(auto& token : tokens)
        {
            if(isdigit(token[0]) || token.length() > 1 && token[0] == '-')
                num.push(atoi(token.c_str()));
            else
            {
                r = num.top(); num.pop();
                l = num.top(); num.pop();
                switch(token[0])
                {
                    case '+':
                        num.push(l + r);
                        break;
                    case '-':
                        num.push(l - r);
                        break;
                    case '*':
                        num.push(l * r);
                        break;
                    case '/':
                        num.push(l / r);
                        break;
                }
            }
        }
        return num.top();
    }
};
```
