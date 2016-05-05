Maximum Gap
==========

## C++

Using sort, O(NlogN) Time
```cpp
class Solution {
public:
    int maximumGap(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int m = 0, N = nums.size();
        for(int i(1); i < N; ++i)
        {
            int tmp = nums[i] - nums[i - 1];
            if(tmp > m) m = tmp;
        }
        return m;
    }
};
```

Using bucket, O(N) Time, O(N) Space
```cpp
class Solution {
public:
    int maximumGap(vector<int>& nums) {
        int N = nums.size();
        if(N < 2) return 0;
        
        int minE = INT_MAX, maxE = INT_MIN;
        for(int n : nums)
        {
            if(n > maxE) maxE = n;
            if(n < minE) minE = n;
        }
        if(maxE == minE) return 0;
        double len = double(maxE - minE)/double(N - 1);
        
        // Record the upper bound and lower bound of each bucket
        vector<int> maxA(N, INT_MIN), minA(N, INT_MAX);
        for(int n : nums)
        {
            int index = (n - minE) / len;
            if(n > maxA[index]) maxA[index] = n;
            if(n < minA[index]) minA[index] = n;
        }
        
        // Find gap between each bucket
        int m = 0, pre = maxA[0];
        for(int i(1); i < N; ++i)
        {
            if(minA[i] == INT_MAX) continue;
            m = max(m, minA[i] - pre);
            pre = maxA[i];
        }
        return m;
    }
};
```
