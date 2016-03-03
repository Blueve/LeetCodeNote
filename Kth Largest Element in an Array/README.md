Kth Largest Element in an Array
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int findKthLargest(vector<int>& nums, int k) {
          priority_queue<int, vector<int>, greater<int>> q;
          for(auto n : nums)
          {
              q.push(n);
              if(q.size() > k) q.pop();
          }
          return q.top();
      }
  };
  ```