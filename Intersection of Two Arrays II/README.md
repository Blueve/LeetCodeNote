Intersection of Two Arrays II
==========

## C++


```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<int, int> hash;
        for(auto n : nums1)
            ++hash[n];
        
        vector<int> result;
        for(auto n : nums2)
        {
            if(hash[n])
            {
                --hash[n];
                result.push_back(n);
            }
        }
        return result;
    }
};
```
