Plus One
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<int> plusOne(vector<int>& digits) {
          int len(digits.size());
          bool c = false;
          for(int i(len - 1); i >= 0; --i)
          {
              if(++digits[i] == 10)
              {
                  digits[i] = 0;
                  c = true;
              }
              else
              {
                  c = false;
                  break;
              }
          }
          if(c) digits.insert(digits.begin(), 1);
          return digits;
      }
  };
  ```
  Better
  ```cpp
  class Solution {
  public:
      vector<int> plusOne(vector<int>& digits) {
          for(int i(digits.size() - 1); i >= 0; --i)
          {
              if(digits[i] == 9)
              {
                  digits[i] = 0;
              }
              else
              {
                  ++digits[i];
                  return digits;
              }
          }
          digits.push_back(0);
          digits[0] = 1;
          return digits;
      }
  };
  ```