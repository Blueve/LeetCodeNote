Single Number III
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<int> singleNumber(vector<int>& nums) {
          unordered_set<int> s;
          for(auto num : nums)
          {
              if(!s.count(num))
                  s.insert(num);
              else
                  s.erase(num);
          }
          
          vector<int> result;
          for(auto num : s)
          {
              result.push_back(num);
          }
          return result;
      }
  };
  ```


  Better
  ```cpp
  class Solution {
  public:
      vector<int> singleNumber(vector<int>& nums) {
          int axorb = nums[0];
          int N = nums.size();
          for(int i(1); i < N; ++i)
          {
              axorb ^= nums[i];
          }
          
          int last = axorb & (~(axorb - 1));
          vector<int> result(2, 0);
          for(int i(0); i < N; ++i)
          {
              if(last & nums[i])
                  result[0] ^= nums[i];
              else
                  result[1] ^= nums[i];
          }
          return result;
      }
  };
  ```