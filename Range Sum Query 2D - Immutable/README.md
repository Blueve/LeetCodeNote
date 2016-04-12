Range Sum Query 2D - Immutable
==========

## C++


```cpp
class NumMatrix {
    vector<vector<int>> sum;
public:
    NumMatrix(vector<vector<int>> &matrix)
    {
        int n = matrix.size();
        int m = n ? matrix[0].size() : 0;
        sum = vector<vector<int>>(n + 1, vector<int>(m + 1, 0));

        for(int i(0); i < n; ++i)
        {
            for(int j(0); j < m; ++j)
            {
                sum[i + 1][j + 1] = matrix[i][j] + sum[i + 1][j] + sum[i][j + 1] - sum[i][j];
            }
        }
    }

    int sumRegion(int row1, int col1, int row2, int col2) {
        row1++, col1++, row2++, col2++;
        return sum[row2][col2] - sum[row1 - 1][col2] - sum[row2][col1 - 1] + sum[row1 - 1][col1 - 1];
    }
};


// Your NumMatrix object will be instantiated and called as such:
// NumMatrix numMatrix(matrix);
// numMatrix.sumRegion(0, 1, 2, 3);
// numMatrix.sumRegion(1, 2, 3, 4);
```
