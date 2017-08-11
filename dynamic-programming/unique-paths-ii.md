# Unique Paths II

> Follow up for "Unique Paths":
>
> Now consider if some obstacles are added to the grids. How many unique paths would there be?
>
> An obstacle and empty space is marked as`1`and`0`respectively in the grid.
>
> For example,
>
> There is one obstacle in the middle of a `3x3` grid as illustrated below.
>
> ```
> [
>   [0,0,0],
>   [0,1,0],
>   [0,0,0]
> ]
> ```
>
> The total number of unique paths is`2`.

原题链接：[https://leetcode.com/problems/unique-paths-ii/\#/description](https://leetcode.com/problems/unique-paths-ii/#/description)

## 题意

与上题 `Unique Path` 的题意类似，只是会增加障碍。

## 解析

解题思路和 `Unique Path` 也是一样，只需要将障碍物所在位置对应的数组元素置为 `0` 即可。不过需要注意的是，对于第一行或第一列的元素，如果存在障碍物，则需要将其后的所有元素所在位置对应的数组元素都置为 `0`，至于理由，你懂的 `^-^`。

## 代码

### C++

```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();
        int arr[m][n];
        for (int i = 0; i < m; i++){
            if (obstacleGrid[i][0] == 1){
                for (int j = i; j < m; j++){
                    arr[j][0] = 0;
                }
                break;
            }
            else{
                arr[i][0] = 1;
            }

        }
        for (int i = 0; i < n; i++){
            if (obstacleGrid[0][i] == 1){
                for (int j = i; j < n; j++){
                    arr[0][j] = 0;
                }
                break;
            }
            else{
                arr[0][i] = 1;
            }
        }
        for (int i = 1; i < m; i++){
            for (int j = 1; j < n; j++){
                if (obstacleGrid[i][j] == 1){
                    arr[i][j] = 0;
                }
                else {
                    arr[i][j] = arr[i][j-1] + arr[i-1][j];
                }
            }
        }
        return arr[m-1][n-1];
    }
};
```

### Java

```java
public class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        int[][] arr = new int[m][n];
        for (int i = 0; i < m; i++){
            if (obstacleGrid[i][0] == 1){
                for (int j = i; j < m; j++){
                    arr[j][0] = 0;
                }
                break;
            }
            else{
                arr[i][0] = 1;
            }

        }
        for (int i = 0; i < n; i++){
            if (obstacleGrid[0][i] == 1){
                for (int j = i; j < n; j++){
                    arr[0][j] = 0;
                }
                break;
            }
            else{
                arr[0][i] = 1;
            }
        }
        for (int i = 1; i < m; i++){
            for (int j = 1; j < n; j++){
                if (obstacleGrid[i][j] == 1){
                    arr[i][j] = 0;
                }
                else {
                    arr[i][j] = arr[i][j-1] + arr[i-1][j];
                }
            }
        }
        return arr[m-1][n-1];
    }
}
```

### Python

```py
class Solution(object):
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        m = len(obstacleGrid);
        n = len(obstacleGrid[0]);
        arr = [[0 for i in range(n)] for j in range(m)];
        for i in range(0, m):
            if obstacleGrid[i][0] == 1:
                for j in range(i, m):
                    arr[j][0] = 0;
                break;
            else:
                arr[i][0] = 1;

        for i in range(0, n):
            if obstacleGrid[0][i] == 1:
                for j in range(i, n):
                    arr[0][j] = 0;
                break;
            else:
                arr[0][i] = 1;

        for i in range(1, m):
            for j in range(1, n):
                if obstacleGrid[i][j] == 1:
                    arr[i][j] = 0;
                else:
                    arr[i][j] = arr[i][j-1] + arr[i-1][j];

        return arr[m-1][n-1];
```



