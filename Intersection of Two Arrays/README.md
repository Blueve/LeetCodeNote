Intersection of Two Arrays
==========

## C++


```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> result, hash;
        for(auto n : nums1)
            hash.insert(n);
        for(auto n : nums2)
            if(hash.count(n))
                result.insert(n);
        return vector<int>(result.begin(), result.end());
    }
};
```
