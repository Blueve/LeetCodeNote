Range Sum Query - Immutable
==========

## C++

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
        auto n = nums.size();
        if(n == 0) return;
        
        sums = vector<int>(n + 1);
        for(int i(0); i < n; ++i)
            sums[i + 1] = sums[i] + nums[i];
    }

    int sumRange(int i, int j) {
        return sums[j + 1] - sums[i];
    }
};
```
