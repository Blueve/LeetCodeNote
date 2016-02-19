Count Primes
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int countPrimes(int n) {
          if(n < 3) return 0;
          
          int N(sqrt(n)), C((n) >> 1), count(0);
          // Only consider odd number
          vector<bool> map(C, true);
          map[3 >> 1] = true;
          for(int i(3); i <= N; i += 2)
          {
              if(map[i >> 1])
              {
                  int inc = i << 1;
                  for(int j(i + inc); j < n; j += inc)
                      map[j >> 1] = false;
              }
          }
          for(auto b : map) b && ++count;
          return count;
      }
  };
  ```
  With cache(Faster when call `countPrimes` more than once)
  ```cpp
  class Solution {
      
  public:
      bool map[1 << 20];
      
      int countPrimes(int n) {
          if(n < 3) return 0;
          
          int N(sqrt(n)), C(n >> 1), count(0);
          map[3 >> 1] = false;
          for(int i(3); i <= N; i += 2)
          {
              if(!map[i >> 1])
              {
                  int inc = i << 1;
                  for(int j(i + inc); j < n; j += inc)
                      map[j >> 1] = true;
              }
          }
          for(int i(0); i < C; ++i) !map[i] && ++count;
          return count;
      }
  };
  ```