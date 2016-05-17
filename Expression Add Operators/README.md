Expression Add Operators
==========

## C++

Generator all possible expression and compute it value
```cpp
class Solution {
    vector<char> ops = { '+', '-', '*' };
public:
    vector<string> addOperators(string num, int target) {
        // Generator all possible expr
        vector<string> result;
        string expr;
        generatorExpr(num, 0, expr, result, target);
        return result;
    }
    
    void generatorExpr(string& num, int p, string& expr, vector<string>& result, int target)
    {
        int len = num.length();
        if(p == len)
        {
            if(computeExpr(expr) == target)
                result.push_back(expr);
            return;
        }   
        if(p == len - 1)
        {
            expr += num[p];
            if(computeExpr(expr) == target)
                result.push_back(expr);
            expr.pop_back();
            return;
        }   
        
        if(num[p] == '0')
        {
            expr += '0';
            for(auto& op : ops)
            {
                expr += op;
                generatorExpr(num, p + 1, expr, result, target);
                expr.pop_back();
            }
            expr.pop_back();
        }
        else
        {
            int back = expr.length();
            for(int i(p); i < len - 1; ++i)
            {
                expr += num.substr(p, i - p + 1);
                for(auto& op : ops)
                {
                    expr += op;
                    generatorExpr(num, i + 1, expr, result, target);
                    expr.pop_back();
                }
                expr.resize(back);
            }
            expr += num.substr(p);
            generatorExpr(num, len, expr, result, target);
            expr.resize(back);
        }
    }
    
    long long computeExpr(string& expr)
    {
        long long len(expr.size()), num(0), result(0), cur(0);
        char op('+');
        for(int i(0); i < len; )
        {
            if(expr[i] == ' ') ++i;
            else if('0' <= expr[i] && expr[i] <= '9')
            {
                num = expr[i] -'0';
                while(++i < len && '0' <= expr[i] && expr[i] <= '9')
                {
                    num *= 10;
                    num += expr[i] - '0';
                }
                switch(op)
                {
                    case '+' : cur += num; break;
                    case '-' : cur -= num; break;
                    case '*' : cur *= num; break;
                }
            }
            else
            {
                op = expr[i++];
                if(op != '*')
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

Better
```cpp
class Solution {
public:
    vector<string> addOperators(string num, int target) {
        vector<string> result;
        generatorExpr(num, "", 0, 0, result, target);
        return result;
    }
    
    void generatorExpr(string num, string expr, long cur, long pre, vector<string>& result, int target)
    {
        int len = num.length();
        if(len == 0)
        {
            if(cur == target)
                result.push_back(expr);
            return;
        }
        
        for(int i(1); i <= len; ++i)
        {
            if(num[0] == '0' && i > 1)
                continue;
                
            auto left = num.substr(0, i);
            auto right = num.substr(i);
            
            auto n = stol(left);
            
            if(expr.empty())
                generatorExpr(right, left, n, n, result, target);
            else
            {
                generatorExpr(right, expr + '+' + left, cur + n, n, result, target);
                generatorExpr(right, expr + '-' + left, cur - n, -n, result, target);
                generatorExpr(right, expr + '*' + left, cur - pre + pre * n, pre * n, result, target);
            }
        }
    }
};
```
