Valid Parentheses
==========

## C++


```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> stack;
        stack.push('#');
        for(auto c : s)
        {
            char top = stack.top();
            if(top == '(' && c == ')' ||
               top == '[' && c == ']' ||
               top == '{' && c == '}')
                stack.pop();
            else
                stack.push(c);
                
        }
        return stack.top() == '#';
    }
};
```

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> stack;
        stack.push('#');
        for(auto c : s)
        {
            char top = stack.top();
            if(c == '(' || c == '[' || c == '{')
                stack.push(c);
            else if(top == '(' && c == ')' ||
                    top == '[' && c == ']' ||
                    top == '{' && c == '}')
                stack.pop();
            else
                return false;
        }
        return stack.top() == '#';
    }
};
```
