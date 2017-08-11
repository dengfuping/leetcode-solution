# Unique Paths

> A robot is located at the top-left corner of a `m x n` grid \(marked 'Start' in the diagram below\).
>
> The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid \(marked 'Finish' in the diagram below\).
>
> How many possible unique paths are there?
>
> ![](https://leetcode.com/static/images/problemset/robot_maze.png)
>
> Above is a `3 x 7` grid. How many possible unique paths are there?
>
> **Note: **m and n will be at most 100.

原题链接：  
[https://leetcode.com/problems/unique-paths/\#/description](https://leetcode.com/problems/unique-paths/#/description)

## 题意

一个机器人在一个 `m * n` 的方格的左上角。机器人只能向右或都向下走一个方格，机器人要到达右下角的方格。请问一共有多少种唯一的路径。其中 `m` 和 `n` 的最大值不超100。

## 解析

典型的动态规划问题。对于数组 `A[m][n]` ，从 `A[0][0]`  到 `A[m-1][n-1]` 有多少条路径。对于数组A中的元素有：

1. 当 `x = 0` 或 `y = 0` 时有 `A[x][y] = 1`；
2. 当 `x >= 1` 且 `y >= 1` 时有递推公式 `A[x][y] = A[x][y-1] + A[x-1][y]`；
3. 所求结果为 `A[m-1][n-1]`。

## 代码

### C++

```cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        int arr[m][n];
        for (int i = 0; i < m; i++){
            arr[i][0] = 1;
        }
        for (int i = 0; i < n; i++){
            arr[0][i] = 1;
        }
        for (int i = 1; i < m; i++){
            for (int j = 1; j < n; j++){
                arr[i][j] = arr[i][j-1] + arr[i-1][j];
            }
        }
        return arr[m-1][n-1];
    }
};
```

### Java

```java
public class Solution {
    public int uniquePaths(int m, int n) {
        int[][] arr = new int[m][n];
        for (int i = 0; i < m; i++){
            arr[i][0] = 1;
        }
        for (int i = 0; i < n; i++){
            arr[0][i] = 1;
        }
        for (int i = 1; i < m; i++){
            for (int j = 1; j < n; j++){
                arr[i][j] = arr[i][j-1] + arr[i-1][j];
            }
        }
        return arr[m-1][n-1];
    }
}
```

### Python

```py
class Solution(object):
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        arr = [[0 for i in range(n)] for j in range(m)];
        for i in range(0, m):
            arr[i][0] = 1;
        for i in range(0, n):
            arr[0][i] = 1;
        for i in range(1, m):
            for j in range(1, n):
                arr[i][j] = arr[i][j-1] + arr[i-1][j];

        return arr[m-1][n-1];
```



