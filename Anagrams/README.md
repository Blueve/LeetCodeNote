Anagrams
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<string> anagrams(vector<string> &strs) {
          map<string, vector<string>> mapSet;
          vector<string> result;
          
          for(int i(0); i < strs.size(); i++)
          {
              string tmp = strs[i];
              sort(tmp.begin(), tmp.end());
              mapSet[tmp].push_back(strs[i]);
          }
          for(auto i(mapSet.begin()); i != mapSet.end(); i++)
          {
              if(i->second.size() > 1)
              {
                  result.insert(result.begin(), i->second.begin(), i->second.end());
              }
          }
          return result;
      }
  };
  ```