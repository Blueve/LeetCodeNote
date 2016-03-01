Different Ways to Add Parentheses
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<int> diffWaysToCompute(string input) {
          vector<int> result;
          int N(input.size());
          
          for(int i(0); i < N; ++i)
          {
              if(input[i] == '+' || input[i] == '-' || input[i] == '*')
              {
                  auto l = diffWaysToCompute(input.substr(0, i));
                  auto r = diffWaysToCompute(input.substr(i + 1));
                  
                  if(input[i] == '+')
                      for(auto a : l)
                          for(auto b : r) result.push_back(a + b);
                  else if(input[i] == '-')
                      for(auto a : l)
                          for(auto b : r) result.push_back(a - b);
                  else
                      for(auto a : l)
                          for(auto b : r) result.push_back(a * b);
              }
          }
          if(result.empty())
              result.push_back(atoi(input.c_str()));
          return result;
      }
  };
  ```
  DP, memorize all input -> result
  ```cpp
  class Solution {
  public:
      vector<int> diffWaysToCompute(string input) {
          map<string, vector<int>> DP;
          return _diffWaysToCompute(input, DP);
      }
      
      vector<int> _diffWaysToCompute(string input, map<string, vector<int>> &DP) {
          vector<int> result;
          int N(input.size());
          
          if(DP.count(input)) return DP[input];
          
          for(int i(0); i < N; ++i)
          {
              if(input[i] == '+' || input[i] == '-' || input[i] == '*')
              {
                  auto l = _diffWaysToCompute(input.substr(0, i), DP);
                  auto r = _diffWaysToCompute(input.substr(i + 1), DP);
                  
                  if(input[i] == '+')
                      for(auto a : l)
                          for(auto b : r) result.push_back(a + b);
                  else if(input[i] == '-')
                      for(auto a : l)
                          for(auto b : r) result.push_back(a - b);
                  else
                      for(auto a : l)
                          for(auto b : r) result.push_back(a * b);
              }
          }
          if(result.empty())
              result.push_back(atoi(input.c_str()));
          
          DP[input] = result;
          return result;
      }
  };
  ```