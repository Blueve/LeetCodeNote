Generate Parentheses
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<string> generateParenthesis(int n) {
          vector<string> result;
          _generateParenthesis(result, n, n);
          return result;
      }
      
      void _generateParenthesis(vector<string> &result, int left, int right, string   item = "")
      {
          if(!left && !right)
              result.push_back(item);
          if(left > 0) // Generate
              _generateParenthesis(result, left - 1, right, item + '(');
          if(right > left) // Comsume
              _generateParenthesis(result, left, right - 1, item + ')');
      }
  };
  ```