Missing Number
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int missingNumber(vector<int>& nums) {
          int N(nums.size()), sum(0);
          int total = N * (N + 1) >> 1;
          
          for(auto num : nums) sum += num;
          return total - sum;
      }
  };
  ```