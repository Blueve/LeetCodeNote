Merge Sorted Array
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
          // Move nums1's elem to back
          for(int i(m - 1); i >= 0; --i)
              nums1[i + n] = nums1[i];
          // Merge
          for(int i(0), j(0), p(0); p < m + n;)
          {
              if(i < m && j < n)
              {
                  if(nums1[i + n] < nums2[j])
                  {
                      nums1[p++] = nums1[n + i++];
                  }
                  else
                  {
                      nums1[p++] = nums2[j++];
                  }
              }
              else if(i == m)
              {
                  while(j != n) nums1[p++] = nums2[j++];
              }
              else // j == n
              {
                  while(i != m) nums1[p++] = nums1[n + i++];
              }
          }
      }
  };
  ```

  Better
  ```cpp
  class Solution {
  public:
      void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
          // Merge from back to front
          // if nums2 merge completed, then merge done.
          for(int p(m + n - 1), i(m - 1), j(n - 1); j >= 0;)
          {
              nums1[p--] = i >= 0 && nums1[i] > nums2[j] ? nums1[i--] : nums2[j--];
          }
      }
  };
  ```