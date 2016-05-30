Median of Two Sorted Arrays
==========

## C++

O(log(M + N)) Time
```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int m = nums1.size(), n = nums2.size();
        int total = m + n;
        if(total & 1)
            return _findMedian(nums1, m, 0, nums2, n, 0, total / 2 + 1);
        else
            return (_findMedian(nums1, m, 0, nums2, n, 0, total / 2) +
                    _findMedian(nums1, m, 0, nums2, n, 0, total / 2 + 1)) / 2;
    }
    
    double _findMedian(vector<int>& nums1, int m, int left1, vector<int>& nums2, int n, int left2, int k)
    {
        if(m > n) return _findMedian(nums2, n, left2, nums1, m, left1, k);
        if(m == 0) return nums2[k - 1];
        if(k == 1) return min(nums1[left1], nums2[left2]);
        int a = min(k / 2, m);
        int b = k - a;
        if(nums1[a + left1 - 1] <= nums2[b + left2 - 1])
            return _findMedian(nums1, m - a, left1 + a, nums2, n, left2, k - a);
        else
            return _findMedian(nums1, m, left1, nums2, n - b, left2 + b, k - b);
    }
};
```
