# Container With Most Water

> Givennnon-negative integersa1,a2, ...,an, where each represents a point at coordinate \(i,ai\).nvertical lines are drawn such that the two endpoints of lineiis at \(i,ai\) and \(i, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.
>
> Note: You may not slant the container andnis at least 2.

原题链接：[https://leetcode.com/problems/container-with-most-water/\#/description](https://leetcode.com/problems/container-with-most-water/#/description)

## 题意

## 解析

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



