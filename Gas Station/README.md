Gas Station
==========

## C++


```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int N(gas.size());

        int gasTank(0), leftSum(INT_MAX), start(0);
        for(int i(0); i < N; ++i)
        {
            gasTank += gas[i] - cost[i];
            // Means gas[i] - cost[i] < Sum(gas[k] - cost[k], 0 -> start - 1)
            if(gasTank < leftSum)
            {
                leftSum = gasTank;
                start = i;
            }
        }
        return (gasTank < 0 ? -1 : (start + 1) % N);
    }
};
```
