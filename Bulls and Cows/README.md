Bulls and Cows
==========

## C++

  - Answer
  One map, two pass
  ```cpp
  class Solution {
  public:
      string getHint(string secret, string guess) {
          char buff[100];
          
          unordered_map<char, int> map;
          int len(secret.size()), countA(0), countB(0);
          
          for(int i(0); i < len; ++i)
          {
              if(secret[i] == guess[i]) continue;
              else ++map[secret[i]];
          }
          
          for(int i(0); i < len; ++i)
          {
              if(secret[i] == guess[i])
                  ++countA;
              else if(map[guess[i]])
              {
                  ++countB;
                  --map[guess[i]];
              }
          }
          sprintf(buff, "%dA%dB", countA, countB);
          return string(buff);
      }
  };
  ```
  Two map, one pass
  ```cpp
  class Solution {
  public:
      string getHint(string secret, string guess) {
          char buff[100];
          unordered_map<char, int> mapS, mapG;
          int len(secret.size()), countA(0), countB(0);
          
          for(int i(0); i < len; ++i)
          {
              if(secret[i] == guess[i]) ++countA;
              else
              {
                  if(mapS[guess[i]] > 0)
                  {
                      ++countB;
                      --mapS[guess[i]];
                  }
                  else ++mapG[guess[i]];
                  if(mapG[secret[i]] > 0)
                  {
                      ++countB;
                      --mapG[secret[i]];
                  }
                  else ++mapS[secret[i]];
              }
          }
          sprintf(buff, "%dA%dB", countA, countB);
          return string(buff);
      }
  };
  ```