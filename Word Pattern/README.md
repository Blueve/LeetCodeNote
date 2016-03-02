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
  Using istringstream
  ```cpp
  class Solution {
  public:
      bool wordPattern(string pattern, string str) {
          unordered_map<char, int> m1;
          unordered_map<string, int> m2;
          
          istringstream is(str);
          string s;
          int i(0);
          for(; is >> s; i++)
          {
              char c = pattern[i];
              if(m1[c] != m2[s]) return false;
              else m1[c] = m2[s] = i + 1;
          }
          return i == pattern.length();
      }
  };
  ```