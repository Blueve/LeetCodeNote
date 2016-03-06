Best Time to Buy and Sell Stock
==========

## C++


```cpp
class Solution {
public:
    int maxProfit(vector<int> &prices) {
        int result = 0;
        int max(0), min, tmp;
        int maxI(-1), minI(0);
        
        if(prices.size() < 2) return 0;
        min = prices[0];
        for(int i(1); i < prices.size(); i++)
        {
            if(prices[i] > prices[i - 1]) // INCING
            {
                if(prices[i] > max)
                {
                    max  = prices[i]; maxI = i;
                }
            }
            else if(prices[i] < prices[i - 1]) // DECING
            {
                if(prices[i] < min)
                {
                    if(minI < maxI) // Try Sell Pre Order
                    {
                        tmp = max - min;
                        result = result > tmp ? result : tmp;
                    }
                    min  = prices[i]; minI = i;
                    max  = prices[i]; maxI = i;
                }
            }
        }
        if(minI < maxI) // Try Sell Pre Order
        {
            tmp = max - min;
            result = result > tmp ? result : tmp;
        }
        return result;
    }
};
```
Better
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        // partial max profit = cur - curMin;
        // max profit = max(partial max frofit, max profit)
        int minPrice(INT_MAX), maxProfit(0);
        for(auto p : prices)
        {
            minPrice = min(p, minPrice);
            maxProfit = max(p - minPrice, maxProfit);
        }
        return maxProfit;
    }
};
```
