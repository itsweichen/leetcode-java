## Unique Paths

> A robot is located at the top-left corner of a *m* x *n* grid (marked 'Start' in the diagram below).
>
> The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
>
> How many possible unique paths are there?

### Solution

很典型的DP题。

```java
// 54%
class Solution {
    public int uniquePaths(int m, int n) {
        int[][] matrix = new int[n][m];
        
        for (int i = 0; i < n; i++) {
            matrix[i][0] = 1;
        }
        
        for (int j = 0; j < m; j++) {
            matrix[0][j] = 1;
        }
        
        for (int i = 1; i < n; i++) {
            for (int j = 1; j < m; j++) {
                matrix[i][j] = matrix[i][j - 1] + matrix[i - 1][j];
            }
        }
        
        return matrix[n - 1][m - 1];
    }
}
```

