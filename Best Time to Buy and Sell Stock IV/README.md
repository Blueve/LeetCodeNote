Best Time to Buy and Sell Stock IV
==========

## C++

For higher k (bigger than N/2), O(N^2) Time,
otherwise O(NK) Time
```cpp
class Solution {
public:
    int maxProfit(int k, vector<int>& prices) {
        int n = prices.size();
        if(!n || !k) return 0;
        // For n days, we can do (n/2) times transaction at most
        // eg. [1,2,1,2,1,2] -> 3 times
        // eg. [1,2,3,4,5,6] -> 1 times
        if(k >= (n >> 1))
        {
            int profit = 0;
            for(int i(1); i < n; ++i)
                profit += max(0, prices[i] - prices[i - 1]);
            return profit;
        }
        
        vector<int> buy(k, INT_MIN), sell(k + 1);
        for(auto p : prices)
        {
            for(int i(0); i < k; ++i)
            {
                sell[i] = max(sell[i], buy[i] + p);
                buy[i] = max(buy[i], sell[i + 1] - p);
            }
        }
        return sell[0];
    }
};
```
