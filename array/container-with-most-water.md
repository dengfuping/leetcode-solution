# Container With Most Water

> Givennnon-negative integers `a1, a2, ..., an`, where each represents a point at coordinate `(i,ai)`. nvertical lines are drawn such that the two endpoints of lineiis at `(i, ai)` and `(i, 0)`. Find two lines, which together with x-axis forms a container, such that the container contains the most water.
>
> Note: You may not slant the container andnis at least 2.

原题链接：[https://leetcode.com/problems/container-with-most-water/\#/description](https://leetcode.com/problems/container-with-most-water/#/description)

## 题意

要找到两条纵线，然后这两条线以及X轴构成的容器能容纳最多的水。

## 解析

容积即面积，它受长和高的影响，当长度减少的时候，高必须增长才有可能提升面积，所以我们从长度最长开始递减，即从两边向中间靠拢， 然后寻找更高的线来弥补长度的减少。

## 代码

### C++

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int max_area = 0;

        while (left < right){
            int area = min(height[left], height[right]) * (right - left);
            max_area = max(max_area, area);
            if (height[left] <= height[right]){
                left++;
            }
            else{
                right--;
            }
        }

        return max_area;
    }
};
```

### Java

```java
public class Solution {
    public int maxArea(int[] height) {
        int left = 0;
        int right = height.length - 1;
        int max_area = 0;

        while (left < right){
            int area = Math.min(height[left], height[right]) * (right - left);
            max_area = Math.max(max_area, area);
            if (height[left] <= height[right]){
                left++;
            }
            else{
                right--;
            }
        }

        return max_area;
    }
}
```

### Python

```py
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        left = 0;
        right = len(height) - 1;
        max_area = 0;

        while left < right:
            area = min(height[left], height[right]) * (right - left);
            max_area = max(max_area, area);
            if height[left] <= height[right]:
                left += 1;
            else:
                right -= 1;

        return max_area;
```



