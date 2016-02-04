Happy Number
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isHappy(int n) {
          unordered_set<int> m;
          int sum(0), number(n), tmp;
          while(true)
          {
              while(number)
              {
                  tmp = number % 10;
                  sum += tmp * tmp;
                  number /= 10;
              }
              if(sum == 1) return true;
              else if(m.count(sum)) return false;
              number = sum;
              m.insert(sum);
              sum = 0;
          }
      }
  }; 
  ```