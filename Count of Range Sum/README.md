Count of Range Sum
==========

## C++

Divide and Conquer(Merge Sort), O(NlogN)
```cpp
class Solution {
public:
    int countRangeSum(vector<int>& nums, int lower, int upper) {
        if(nums.empty())
            return 0;
        long s = 0;
        vector<long> sum(1);
        for(auto n : nums)
            sum.push_back(s += n);
            
        return _countRangeSum(sum, lower, upper, 0, sum.size());
    }
    
    int _countRangeSum(vector<long>& sum, int lower, int upper, int l, int r)
    {
        if(l == r - 1)
            return 0;
        
        // Count two parts    
        int m = l + (r - l >> 1);
        int count = _countRangeSum(sum, lower, upper, l, m) + 
                    _countRangeSum(sum, lower, upper, m, r);
        
        // Count between two parts
        int x, y;
        x = y = m;
        for(int i(l); i < m; ++i)
        {
            while(x < r && sum[x] - sum[i] < lower)
                ++x;
            while(y < r && sum[y] - sum[i] <= upper)
                ++y;
            count += y - x;
        }
        /* The code before can be also written by this form:
        auto b1 = sum.begin() + m, b2 = b1, e = sum.begin() + r;
        for(int i(l); i < m; ++i)
        {
            count += (b1 = upper_bound(b1, e, upper + sum[i])) -
                     (b2 = lower_bound(b2, e, lower + sum[i]));
        }
        */
        
        // Merge two part
        int n = r - l, i = 0, left = l, right = m;
        vector<long> tmp(n);
        while(left < m && right < r)
        {
            if(sum[left] <= sum[right])
                tmp[i++] = sum[left++];
            else
                tmp[i++] = sum[right++];
        }
        while(left < m)
            tmp[i++] = sum[left++];
        while(right < r)
            tmp[i++] = sum[right++];
        copy(tmp.begin(), tmp.end(), sum.begin() + l);
        return count;
    }
};
