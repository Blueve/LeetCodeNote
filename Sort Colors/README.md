Sort Colors
==========

## C++

  - Answer
  Two pass
  ```cpp
  class Solution {
  public:
      void sortColors(vector<int>& nums) {
          int counter[3] = {0}, p(0);
          for(auto n : nums) ++counter[n];
          
          for(int i(0); i < 3; ++i)
          {
              while(counter[i]--) nums[p++] = i;
          }
      }
  };
  ```

  One pass
  ```cpp
  class Solution {
  public:
      void sortColors(vector<int>& nums) {
          int p0(0), p2(nums.size() - 1);
          for(int p1(0); p1 <= p2;)
          {
              if(nums[p1] == 0) swap(nums[p0++], nums[p1++]);
              else if(nums[p1] == 1) ++p1;
              else swap(nums[p1], nums[p2--]);
          }
      }
  };
  ```