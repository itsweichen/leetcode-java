## Number of Islands

> Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

### Solution

看看 Union Find - https://leetcode.com/problems/number-of-islands/discuss/56354/1D-Union-Find-Java-solution-easily-generalized-to-other-problems



**DFS**

注意 call dfs 函数的先决条件，漏写一个check就stackoverflow了。

另一种或许更好地方法是把所有check都放在子函数里面。

```java
// 23%
// cannot find symbol! 写子函数的时候注意哪些变量要传入！
class Solution {
    public int numIslands(char[][] grid) {
        if (grid.length == 0) return 0;
        
        int m = grid.length;
        int n = grid[0].length;
        
        boolean[][] visited = new boolean[m][n]; // default will be false
        int numIslands = 0;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (!visited[i][j] && grid[i][j] == '1') {
                    dfs(i, j, visited, grid);
                    numIslands++;
                }
            }
        }
        
        return numIslands;
    }
    
    private void dfs(int ci, int cj, boolean[][] visited, char[][] grid) {
        visited[ci][cj] = true;
        
        int[][] pos = pos(ci, cj);
        for (int p = 0; p < 4; p++) {
            int i = pos[p][0];
            int j = pos[p][1];
            
            boolean isValidPos = false;
            if (i >= 0 && j >= 0 && i < grid.length && j < grid[0].length) {
                isValidPos = true;
            }
            if (isValidPos && grid[i][j] == '1' && !visited[i][j]) { // && !visited[i][j]
                dfs(i, j, visited, grid);
            }
        }
    }
    
    private int[][] pos(int i, int j) {
        return new int[][] {
            {i - 1, j}, {i + 1, j}, {i, j - 1}, {i, j + 1}
        };
    }
}
```

在 dfs 子函数里check. 减少调用函数的条件。这样唯一的条件就是 `i` 和 `j` 要是valid的。

```java
// cannot find symbol! 写子函数的时候注意哪些变量要传入！
class Solution {
    public int numIslands(char[][] grid) {
        if (grid.length == 0) return 0;
        
        int m = grid.length;
        int n = grid[0].length;
        
        boolean[][] visited = new boolean[m][n]; // default will be false
        int numIslands = 0;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (dfs(i, j, visited, grid)) {
                    numIslands++;
                }
            }
        }
        
        return numIslands;
    }
    
    private boolean dfs(int ci, int cj, boolean[][] visited, char[][] grid) {
        if (visited[ci][cj] || grid[ci][cj] != '1') {
            return false;
        }
        
        visited[ci][cj] = true;
        
        int[][] pos = pos(ci, cj);
        for (int p = 0; p < 4; p++) {
            int i = pos[p][0];
            int j = pos[p][1];
            
            boolean isValidPos = false;
            if (i >= 0 && j >= 0 && i < grid.length && j < grid[0].length) {
                isValidPos = true;
            }
            if (isValidPos) {
                dfs(i, j, visited, grid);
            }
        }
        
        return true;
    }
    
    private int[][] pos(int i, int j) {
        return new int[][] {
            {i - 1, j}, {i + 1, j}, {i, j - 1}, {i, j + 1}
        };
    }
}
```

