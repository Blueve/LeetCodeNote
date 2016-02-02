Best Time to Buy and Sell Stock II
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      const int INC = 1;
      const int DEC = 2;
      
      int maxProfit(vector<int> &prices) {
          int min;
          int result(0);
          
          int flag(DEC);
          
          if(prices.size() < 2) return 0;
          for(int i(1); i < prices.size(); i++)
          {
              if(prices[i] < prices[i - 1] && flag != DEC)
              {
                  flag = DEC;
                  result += prices[i - 1] - min;
              }
              else if(prices[i] > prices[i - 1] && flag != INC)
              {
                  flag = INC;
                  min = prices[i - 1]; // BUY
              }
          }
          if(flag == INC) result += prices[prices.size() - 1] - min;
          return result;
      }
  };
  ```

  Better
  ```cpp
  class Solution {
  public:
      int maxProfit(vector<int>& prices) {
          int profit(0), diff;
          int N(prices.size());
          for(int i(1); i < N; ++i)
          {
              diff = prices[i] - prices[i - 1];
              if(diff > 0) profit += diff; 
          }
          return profit;
      }
  };
  ```