Range Sum Query - Immutable
==========

## C++

  - Answer
  Short answer
  ```cpp
  class NumArray {
      vector<int> sums;
  public:
      NumArray(vector<int> &nums) {
          sums.push_back(0);
          for(auto num : nums)
              sums.push_back(sums.back() + num);
      }
  
      int sumRange(int i, int j) {
          return sums[j + 1] - sums[i];
      }
  };
  ```
  Faster
  ```cpp
  class NumArray {
      vector<int> sums;
  public:
      NumArray(vector<int> &nums) {
          sums.push_back(0);
          for(auto num : nums)
              sums.push_back(sums.back() + num);
      }
  
      int sumRange(int i, int j) {
          return sums[j + 1] - sums[i];
      }
  };
  ```