Best Time to Buy and Sell Stock III
==========

## C++

O(N) Space, Considering two case (Do one or two transactions)
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        if(!n) return 0;
        
        vector<int> firstBuy(n), firstSell(n),
                    secondBuy(n), secondSell(n);
        // Do one transaction
        firstBuy[0] = -prices[0];
        for(int i = 1; i < n; ++i)
        {
            firstBuy[i] = max(firstBuy[i - 1], -prices[i]);
            firstSell[i] = max(firstSell[i - 1], firstBuy[i - 1] + prices[i]);
        }
        if(n == 1) return firstSell[1];
        // Do two transactions
        secondBuy[1] = firstSell[1] - prices[1];
        for(int i = 2; i < n; ++i)
        {
            secondBuy[i] = max(secondBuy[i - 1], firstSell[i - 1] - prices[i]);
            secondSell[i] = max(secondSell[i - 1], secondBuy[i - 1] + prices[i]);
        }
        return max(firstSell[n - 1], secondSell[n - 1]);
    }
};
```

O(N) Space, Can do second buy and first sell at same day
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        if(!n) return 0;
        
        vector<int> firstBuy(n, INT_MIN), firstSell(n),
                    secondBuy(n, INT_MIN), secondSell(n);
        firstBuy[0] = secondBuy[0] = -prices[0];
        for(int i(1); i < n; ++i)
        {
            firstBuy[i]   = max(firstBuy[i - 1],   -prices[i]);
            firstSell[i]  = max(firstSell[i - 1],  firstBuy[i - 1] + prices[i]);
            secondBuy[i]  = max(secondBuy[i - 1],  firstSell[i - 1] - prices[i]);
            secondSell[i] = max(secondSell[i - 1], secondBuy[i - 1] + prices[i]);
        }
        return secondSell.back();
    }
};
```

Better, O(1) Space
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int firstBuy(INT_MIN), firstSell(0), secondBuy(INT_MIN), secondSell(0);
        for(auto p : prices)
        {
            secondSell = max(secondSell, secondBuy + p);
            secondBuy  = max(secondBuy,  firstSell - p);
            firstSell  = max(firstSell,  firstBuy + p);
            firstBuy   = max(firstBuy,   -p);
        }
        return secondSell;
    }
};
```
