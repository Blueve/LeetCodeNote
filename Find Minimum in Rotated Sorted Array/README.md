Find Minimum in Rotated Sorted Array
==========

## C++

  - Answer
  Consider 3 situation:
  low mid highest lowest high
  low highest lowest mid high
  lowest mid highest

  ```cpp
  class Solution {
  public:
      int findMin(vector<int>& nums) {
          int l(0), r(nums.size() - 1), m(0);
          while(l < r)
          {
              m = l + ((r - l) >> 1);
              if(nums[m] < nums[l]) r = m;
              else                  l = m + 1;
          }
          return nums[l];
      }
  };
  ```