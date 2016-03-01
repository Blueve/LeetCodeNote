Increasing Triplet Subsequence
==========

## C++

  - Answer

  Same as `Longest Increasing Subsequence`

  ```cpp
  class Solution {
  public:
      bool increasingTriplet(vector<int>& nums) {
          int tri[3], p(0);
          if(nums.size() < 3) return false;
          tri[0] = nums[0];
          for(auto i : nums)
          {
              if(i > tri[p]) tri[++p] = i;
              else
              {
                  for(int k(0); k <= p; ++k)
                      if(i <= tri[k])
                      {
                          tri[k] = i; break;
                      }
              }
              if(p == 2) return true;
          }
          return false;
      }
  };
  ```
  Better
  ```cpp
  class Solution {
  public:
      bool increasingTriplet(vector<int>& nums) {
          int A(INT_MAX), B(INT_MAX);
          for(auto i : nums)
          {
              if(i > B) return true;
              else if(i <= B && i > A) B = i;
              else A = i;
          }
          return false;
      }
  };
  ```