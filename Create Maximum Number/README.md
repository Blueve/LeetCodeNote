Create Maximum Number
==========

## C++


```cpp
class Solution {
public:
    vector<int> maxNumber(vector<int>& nums1, vector<int>& nums2, int k) {
        int n = nums1.size();
        int m = nums2.size();
        vector<int> result(k);
        for(int i = max(0, k - m); i <= k && i <= n; ++i)
        {
            auto a = maxNumber(nums1, i);
            auto b = maxNumber(nums2, k - i);
            auto r = merge(a, b, k);
            if(greater(r, 0, result, 0))
                result = r;
        }
        return result;
    }
    
    vector<int> merge(vector<int>& nums1, vector<int>& nums2, int k)
    {
        vector<int> result(k);
        for(int i = 0, j = 0, r = 0; r < k; ++r)
            result[r] = greater(nums1, i, nums2, j) ? nums1[i++] : nums2[j++];
        return result;
    }
    
    bool greater(vector<int>& nums1, int i, vector<int>& nums2, int j)
    {
        while(i < nums1.size() && j < nums2.size() && nums1[i] == nums2[j])
            ++i, ++j;
        return j == nums2.size() ||
               i < nums1.size() && nums1[i] > nums2[j];
    }
    
    vector<int> maxNumber(vector<int>& nums, int k)
    {
        int n = nums.size();
        vector<int> result(k);
        for(int i = 0, j = 0; i < n; ++i)
        {
            while(n - i + j > k && j > 0 && result[j - 1] < nums[i])
                --j;
            if(j < k)
                result[j++] = nums[i];
        }
        return result;
    }
};
```
