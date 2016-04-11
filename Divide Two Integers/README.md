Divide Two Integers
==========

## C++


```cpp
class Solution {
public:
    int divide(int dividend, int divisor) {
        int result(0);
        
        if(divisor == 0) return INT_MAX;
        
        int symbol = 1;
        if((dividend < 0 && divisor > 0) || 
           (dividend > 0 && divisor < 0))
            symbol = -1;
        
        dividend = -abs(dividend);
        divisor = -abs(divisor);
        
        vector<int> arr(1, divisor);
        while(arr.back() > dividend && arr.back() >= (INT_MIN >> 1))
            arr.push_back(arr.back() << 1);
        
        int l, r = arr.size() - 1, m;
        while(dividend <= arr[0])
        {
            l = 0;
            while(l <= r)
            {
                m = l + (r - l >> 1);
                if(arr[m] < dividend) r = m - 1;
                else if(arr[m] > dividend) l = m + 1;
                else break;
            }
            result += 1 << r;
            dividend -= arr[r];
        }
        if(symbol == 1 && result == INT_MIN) return INT_MAX;
        return symbol * result;
    }
};
```
```cpp
class Solution {
public:
    int divide(int dividend, int divisor) {
        int result(0);
        
        if(divisor == 0 || (dividend == INT_MIN && divisor == -1))
            return INT_MAX;
        
        int symbol = ((dividend < 0) ^ (divisor < 0)) ? -1 : 1;
        dividend = -abs(dividend);
        divisor = -abs(divisor);
        
        vector<int> arr(1, divisor);
        while(arr.back() > dividend && arr.back() >= (INT_MIN >> 1))
            arr.push_back(arr.back() << 1);
        
        int r = arr.size() - 1;
        while(dividend <= arr[0])
        {
            while(arr[r] < dividend)
                --r;
            result += 1 << r;
            dividend -= arr[r];
        }
        return symbol * result;
    }
};
```
