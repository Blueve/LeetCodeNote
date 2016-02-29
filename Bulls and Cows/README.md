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
  Shorter and reduce memory used
  ```cpp
  class Solution {
  public:
      string getHint(string secret, string guess) {
          int length(secret.length()),sumA(0), sumB(0);
          int countS[10] = {0}, countG[10] = {0};
          for(int i(0); i < length; i++)
          {
              
              if(secret[i] == guess[i]) sumA++;
              else
              {
                  int s(secret[i] - '0'), g(guess[i] - '0');
                  (countS[g] > 0) ? countS[g]--, sumB++ : countG[g]++;
                  (countG[s] > 0) ? countG[s]--, sumB++ : countS[s]++;
              }
          }
          return to_string(sumA) + 'A' + to_string(sumB) + 'B';
      }
  };
  ```