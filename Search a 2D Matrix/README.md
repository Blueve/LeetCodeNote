Search a 2D Matrix
==========

## C++


```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int M(matrix.size()), N(matrix[0].size());
        int l(0), r(M - 1), m, i;
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if(target > matrix[m][0]) l = m + 1;
            else if(target < matrix[m][0]) r = m - 1;
            else return true;
        }
        if(r == -1 || l == 0) return false;
        i = l - 1;
        l = 0; r = N - 1;
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if(target > matrix[i][m]) l = m + 1;
            else if(target < matrix[i][m]) r = m - 1;
            else return true;
        }
        return false;
    }
};
```
Better, treat 2D-array as 1D-array
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int M(matrix.size()), N(matrix[0].size());
        int l(0), r(M * N - 1), m;
        while(l <= r)
        {
            m = l + (r - l >> 1);
            if     (target > matrix[m / N][m % N]) l = m + 1;
            else if(target < matrix[m / N][m % N]) r = m - 1;
            else return true;
        }
        return false;
    }
};
```
