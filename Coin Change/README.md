Coin Change
==========

## C++


```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        vector<int> DP(amount + 1, INT_MAX);
        DP[0] = 0;
        for(int i = 0; i <= amount; ++i)
        {
            if(DP[i] == INT_MAX) continue;
            for(auto coin : coins)
            {
                if(coin + i <= amount)
                    DP[i + coin] = min(DP[i] + 1, DP[i + coin]);
            }
        }
        return (DP[amount] == INT_MAX ? - 1 : DP[amount]);
    }
};
```
Better
```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        vector<int> DP(amount + 1, amount + 1);
        DP[0] = 0;
        for(auto coin : coins)
        {
            for(int i = coin; i <= amount; ++i)
            {
                DP[i] = min(DP[i - coin] + 1, DP[i]);
            }
        }
        return (DP[amount] > amount ? - 1 : DP[amount]);
    }
};
```