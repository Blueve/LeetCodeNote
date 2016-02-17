Word Pattern
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool wordPattern(string pattern, string str) {
          map<char, int> mapA;
          map<string, int> mapB;
          int plen(pattern.size()), slen(str.size()), p(0), i(0), start(0), count;
          
          while(i < slen)
          {
              // find a word
              count = 0;
              while(i < slen && str[i++] != ' ') ++count;
              string word = str.substr(start, count);
              
              if(p == plen || mapA[pattern[p]] != mapB[word])
                  return false;
              else
                  mapA[pattern[p++]] = mapB[word] = p + 1;
              
              start = i;
          }
          return p == plen;
      }
  };
  ```