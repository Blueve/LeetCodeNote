Best Time to Buy and Sell Stock with Cooldown
==========

## C++

  - Answer

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