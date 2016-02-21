Rotate Array
==========

## C++

  - Answer
  O(K) Space O(N) Time
  ```cpp
  class Solution {
  public:
      void rotate(vector<int>& nums, int k) {
          int N(nums.size());
          k %= N;
          vector<int> tmp(nums.begin() + (N - k), nums.end());
          for(int i(N - 1); i >= k; --i) 
              nums[i] = nums[i - k];
          for(int i(0); i < k; ++i)
              nums[i] = tmp[i];
      }
  };
  ```
  O(1) Space O(N) Time
  ```cpp
  class Solution {
  public:
      void rotate(vector<int>& nums, int k) {
          int N(nums.size());
          if(!(k %= N)) return;
          reverse(nums.begin() + (N - k), nums.end());
          reverse(nums.begin(), nums.end());
          reverse(nums.begin() + k, nums.end());
      }
  };
  ```