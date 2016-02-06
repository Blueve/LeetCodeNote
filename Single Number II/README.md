Single Number II
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int singleNumber(vector<int>& nums) {
          int result(0), bitSum, bitMask, N(nums.size());
          for(int i(0); i < 32; ++i)
          {
              bitMask = 1 << i;
              bitSum = 0;
              for(auto num : nums)
              {
                  bitSum += num & bitMask ? 1 : 0;
              }
              if(bitSum % 3) result |= bitMask;
          }
          return result;
      }
  };
  ```
  Better - using Karnaugh map to analyze
  ```cpp
  class Solution {
  public:
      int singleNumber(vector<int>& nums) {
          int bitOne(0), bitTwo(0);
          for(auto num : nums)
          {
              bitOne = (~bitTwo) & (bitOne ^ num);
              bitTwo = (~bitOne) & (bitTwo ^ num);
          }
          return bitOne;
      }
  };
  ```