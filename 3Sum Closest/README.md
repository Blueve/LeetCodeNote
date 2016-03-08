3Sum Closest
==========

## C++


```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int N(nums.size()), sum, result;
        
        sort(nums.begin(), nums.end());
        
        // 1 2 3 4 5 6 7 8
        // i[j  ->   <-  k]
        for(int i(0); i < N; ++i)
        {
            int j(i + 1), k(N - 1);
            while(j < k)
            {
                sum = nums[i] + nums[j] + nums[k];
                if(abs(sum - target) < abs(result - target))
                {
                    result = sum;
                    if(result == target) return result;
                }
                sum > target ? --k: ++j;
            }
        }
        return result;
    }
};
```
