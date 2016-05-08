Wiggle Sort II
==========

## C++

O(logN) Time, O(N) Space
```cpp
class Solution {
public:
    void wiggleSort(vector<int>& nums) {
        int n = nums.size();
        auto tmp = nums;
        sort(tmp.begin(), tmp.end());
        for (int i = n - 1, j = 0, k = i / 2 + 1; i >= 0; i--)
            nums[i] = tmp[i & 1 ? k++ : j++];
    }
};
```
