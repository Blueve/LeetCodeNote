Best Time to Buy and Sell Stock with Cooldown
==========

## C++


```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int N(prices.size()), maxProfit(0);
        vector<int> sell(N), buy(N);
        if(!N) return 0;
        buy[0] = -prices[0];
        for(int i(1); i < N; ++i)
        {
            buy[i] = max(sell[i - 2] - prices[i], buy[i - 1]);
            sell[i] = max(prices[i] + buy[i - 1], sell[i - 1]);
        }
        return sell[N - 1];
    }
};
```
Better
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if(!prices.size()) return 0;
        int sell(0), preSell(0), buy(-prices[0]), preBuy;
        for(auto p : prices)
        {
            preBuy = buy;
            buy = max(buy, preSell - p);
            
            preSell = sell;
            sell = max(sell, preBuy + p);
        }
        return sell;
    }
};
```
Consider sell and cd but buy
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int N(prices.size());
        int pre(0), sellP(0), coolP(0);
        for(int i(1); i < N; i++)
        {
            pre = sellP;
            sellP = max(sellP + prices[i] - prices[i - 1], coolP);
            coolP = max(pre, coolP);
        }
        return max(sellP, coolP);
    }
};
```
