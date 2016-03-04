Verify Preorder Serialization of a Binary Tree
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isValidSerialization(string preorder) {
          int len(preorder.size()), l(0), check(1);
          for(int i(0); i < len && check; ++i)
          {
              if(preorder[i] == ',')
              {
                  (preorder[i - 1] == '#') ? --check : ++check;
              }
          }
          return check == 1 && preorder.back() == '#';
      }
  };
  ```