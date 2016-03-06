Pascal's Triangle
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        int *tmp = new int[numRows + 1]{0};
        tmp[0] = 1;
        vector<vector<int>> result(numRows, vector<int>());
        for(int i(0); i < numRows; ++i)
        {
            for(int j(0); j <= i; ++j)
            {
                result[i].push_back(tmp[j]);
            }
            for(int j(0); j <= i; ++j)
            {
                tmp[j + 1] = result[i][j] + tmp[j + 1];
            }
        }
        return result;
    }
};
```
Better
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result(numRows);
        for(int i(0); i < numRows; ++i)
        {
            result[i].resize(i + 1);
            result[i][0] = result[i][i] = 1;
            
            for(int j(1); j < i; ++j)
            {
                result[i][j] = result[i - 1][j - 1] + result[i - 1][j];
            }
        }
        return result;
    }
};
```
