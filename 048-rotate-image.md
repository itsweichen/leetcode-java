## Rotate Image

> You are given an *n* x *n* 2D matrix representing an image.
>
> Rotate the image by 90 degrees (clockwise).

### Solution

一层一层转。关键在于把问题分解成，找到规律。

```java
// 98.98%
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for (int k = 0; k < n / 2; k++) {
            int top = k;
            int bottom = n - k - 1;
            int left = k;
            int right = n - k - 1;
            for (int p = 0; p < n - 2 * k - 1; p++) {
                int tmp = matrix[top][left + p];
                matrix[top][left + p] = matrix[bottom - p][left];
                matrix[bottom - p][left] = matrix[bottom][right - p];
                matrix[bottom][right - p] = matrix[top + p][right];
                matrix[top + p][right]= tmp;
            }
        }
    }
}
```

