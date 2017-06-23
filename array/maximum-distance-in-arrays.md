# Maximum Distance in Arrays

> Given m arrays, and each array is sorted in ascending order. Now you can pick up two integers from two different arrays \(each array picks one\) and calculate the distance. We define the distance between two integers a and b to be their absolute difference \|a-b\|. Your task is to find the maximum distance.

## 题意

在给出的m个已排序（升序）数组中，任取两个数组并从中分别取出两个整数a和b，我们的任务就是要找到\|a-b\|的最大值。

## 解析

遍历各个数组，将本组的最小值与其他组的最大值依次做差，再将本组的最大值与其他组的最小依次做差，逐一比较他们的绝对值以后取较大者即可。

## 代码

### C++

```cpp
class Solution {
public:
    int maxDistance(vector<vector<int>>& arrays) {
        int ret = 0;
        int m = arrays.size();
        for (int i = 0; i < m - 1; i++){
            int n = arrays[i].size();

            for(int j = i + 1; j < m; j++){
                int p = arrays[j].size();

                ret = max(ret, abs(arrays[i][0] - arrays[j][p-1]));
                ret = max(ret, abs(arrays[i][n-1] - arrays[j][0]));
            }
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
        for (int i = 0; i < m - 1; i++){
            int n = arrays.get(i).size();
            
            for (int j = i + 1; j < m; j++){
                int p = arrays.get(j).size();
                
                ret = Math.max(ret, Math.abs(arrays.get(i).get(0) - arrays.get(j).get(p-1)));
                ret = Math.max(ret, Math.abs(arrays.get(i).get(n-1) - arrays.get(j).get(0)));
            }
        }
        
        return ret;
    }
}
```

### Python



