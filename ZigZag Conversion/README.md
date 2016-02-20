ZigZag Conversion
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      string convert(string s, int numRows) {
          if(numRows == 1) return s;
          
          vector<string> table(numRows);
          vector<int> step((numRows - 1) << 1);
          string result;
          // Generate step table
          int i(0), half(numRows - 1), full((numRows - 1) << 1);
          for(int i(0); i < half; ++i) step[i] = 1;
          for(int i(0); i < half; ++i) step[half + i] = -1;
          
          int p(0);
          i = 0;
          for(auto c : s)
          {
              table[i] += c;
              i += step[p++ % full];
          }
          
          for(auto item : table) result += item;
          return result;
      }
  };
  ```
  Without step table
  ```cpp
  class Solution {
  public:
      string convert(string s, int numRows) {
          if(numRows == 1) return s;
          
          vector<string> table(numRows);
          string result;
          
          int i(0), inc(1), half(numRows - 1);
          for(auto c : s)
          {
              table[i] += c;
              if(i == 0) inc = 1;
              else if(i == half) inc = -1;
              i += inc;
          }
          
          for(auto item : table) result += item;
          return result;
      }
  };
  ```