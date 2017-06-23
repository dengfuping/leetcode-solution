# Maximum Distance in Arrays

> Given m arrays, and each array is sorted in ascending order. Now you can pick up two integers from two different arrays \(each array picks one\) and calculate the distance. We define the distance between two integers a and b to be their absolute difference \|a-b\|. Your task is to find the maximum distance.

## 题意

在给出的m个已排序（升序）数组中，任取两个数组并从中分别取出两个整数a和b，我们的任务就是要找到\|a-b\|的最大值。

## 解析

一趟遍历，将本组的最小值与其他组的最大值依次做差，再将本组的最大值与其他组的最小依次做差，取绝对值比较后取较大者即可。

## 代码

### C++

```cpp
class Solution {
public:
    int maxDistance(vector<vector<int>>& arrays) {
        int ret = 0;
        int m = arrays.size();
        int minValue = arrays[0][0];
        int maxValue = arrays[0][arrays[0].size() - 1];
        for (int i = 1; i < m; i++){
            int n = arrays[i].size();
            ret = max(ret, abs(minValue - arrays[i][n-1]));
            ret = max(ret, abs(maxValue - arrays[i][0]));
            minValue = min(minValue, arrays[i][0]);
            maxValue = max(maxValue, arrays[i][n-1]);
        }

        return ret;
    }
};
```

### Java

```java
public class Solution {
    public int maxDistance(List<List<Integer>> arrays) {
        int ret = 0;
        int m = arrays.size();
        int minValue = arrays.get(0).get(0);
        int maxValue = arrays.get(0).get(arrays.get(0).size() - 1);

        for (int i = 1; i < m; i++) {
            int n = arrays.get(i).size();
            ret = Math.max(ret, Math.abs(minValue - arrays.get(i).get(n-1)));
            ret = Math.max(ret, Math.abs(maxValue - arrays.get(i).get(0)));
            minValue = Math.min(minValue, arrays.get(i).get(0));
            maxValue = Math.max(maxValue, arrays.get(i).get(n - 1));
        }

        return ret;
    }
}
```

### Python

```py
class Solution:
    def maxDistance(self, arrays):
        """
        :type arrays: List[List[int]]
        :rtype: int
        """
        ret = 0;
        m = len(arrays);
        minValue = arrays[0][0];
        maxValue = arrays[0][len(arrays[0])-1];
        for i in range(1, m):
            n = len(arrays[i]);
            ret = max(ret, abs(minValue - arrays[i][n-1]));
            ret = max(ret, abs(maxValue - arrays[i][0]));
            minValue = min(minValue, arrays[i][0]);
            maxValue = max(maxValue, arrays[i][n-1]);

        return ret;
```

## 复杂度分析

很明显，只对数组进行了一次遍历，时间复杂度为O\(n\)。



