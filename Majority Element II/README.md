Majority Element II
==========

## C++


```cpp
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        if(nums.empty()) return {};
        // At most two majority elem
        int A, B;
        int counterA(0), counterB(0), N(nums.size() / 3);
        
        // Find top 2 frequent elem
        for(auto n : nums)
        {
            if(A == n) ++counterA;
            else if(B == n) ++counterB;
            else if(!counterA)
            {
                A = n; counterA = 1;
            }
            else if(!counterB)
            {
                B = n; counterB = 1;
            }
            else
            {
                --counterA; --counterB;
            }
        }
        
        // Check
        counterA = counterB = 0;
        for(auto n : nums)
        {
            if(A == n) ++counterA;
            else if(B == n) ++counterB;
        }
        
        vector<int> result;
        if(counterA > N) result.push_back(A);
        if(counterB > N) result.push_back(B);
        return result;
    }
};
```
