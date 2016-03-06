Find Peak Element
==========

## C++


```cpp
class Solution {
public:

    int findPeakElement(vector<int>& nums) {
        // Given index must in the peek left/right/it self/valley
        int N(nums.size() - 1);
        int l(0), r(N), m;
        int left, right;
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if((m > 0 && nums[m - 1] > nums[m]) && 
               (m < N && nums[m] > nums[m + 1] || m == N))
                r = m - 1;
            else if((m > 0 && nums[m - 1] < nums[m] || m == 0) && 
                    (m < N && nums[m] < nums[m + 1]))
                l = m + 1;
            else if((m > 0 && nums[m - 1] > nums[m]) && 
                    (m < N && nums[m] < nums[m + 1]))
                (m - l > r - m) ? (r = m - 1) : (l = m + 1);
            else
                return m;
        }
        return m;
    }
};
```
Simpler, slower convergence
```cpp
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        // Given index must in the peek left/right
        int N(nums.size() - 1);
        int l(0), r(N), m;
        int left, right;
        while(l < r)
        {
            m = l + (r - l >> 1);
            if(nums[m] < nums[m + 1]) l = m + 1;
            else r = m;
        }
        return l;
    }
};
```
