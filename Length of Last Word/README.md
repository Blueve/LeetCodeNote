Length of Last Word
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int lengthOfLastWord(string s) {
          int len(s.size()), count(0), i;
          // Skip spaces
          for(i = len - 1; len >= 0; --i)
              if(s[i] != ' ') break;
          
          while(i >= 0 && s[i--] != ' ') count++;
          
          return count;
      }
  };
  ```