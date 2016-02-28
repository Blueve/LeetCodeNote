Container With Most Water
==========

## C++

  - Answer
  Consider it from wide to narrow, only higer height can make sum bigger.
  ```cpp
  class Solution {
  public:
      int maxArea(vector<int>& height) {
          int N(height.size()), l(0), r(N - 1), sum;
          
          while(l < r)
          {
              sum = max(sum, (r - l) * min(height[l], height[r]));
              if(height[l] < height[r]) ++l;
              else --r;
          }
          return sum;
      }
  };
  ```