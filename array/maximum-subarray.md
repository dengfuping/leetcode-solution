# Maximum Subarray

> Find the contiguous subarray within an array \(containing at least one number\) which has the largest sum.
>
> For example, given the array`[-2,1,-3,4,-1,2,1,-5,4]`,  
> the contiguous subarray`[4,-1,2,1]`has the largest sum =`6`.

原题链接：[https://leetcode.com/problems/maximum-subarray/\#/description](https://leetcode.com/problems/maximum-subarray/#/description)

## 题意

在一个数组中找出一个连续的子数组使其具有最大和。

## 解析

这题乍一看，似乎解题思路很简单，不就是遍历求和再比较嘛。但长度为n的数组，其连续的子数组个数是 `2^n`，需要嵌套循环才可遍历，时间复杂度为 `O(n^3)`（因为求和也需要遍历）。这样的话复杂度过高，`LeetCode` 上也无法通过，显然不是我们想要的最佳解决方案。

也许我们可以换一种思路。对于数组 `array[1...n]`，假设 `array[i...j]` 是满足最大和要求的连续子数组。那么无论对于什么 `k(i <= k <= j)`，我们都有 `array[i...k] < 0`。因为如果 `array[i...k] > 0`，说明还存在 `array[k...j] > array[i...j]`，即假设中的 `array[i...j]` 不是满足最大和要求的连续子数组。换句话说，如果遇到和小于0的连续子数组，那它必然不被包含在所求数组中，可以直接舍弃掉。这样的话，就能避免前面方法带来的不必要的遍历过程，将时间复杂度降至 `O(n)`。

## 代码

### C++

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max = INT_MIN;
        int sum = 0;
        for (int i = 0; i < nums.size(); i++){
            sum += nums[i];
            if (sum > max){
                max = sum;
            }
            if (sum < 0){
                sum = 0;
            }
        }
        return max;
    }
};
```

### Java

```java
public class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        int sum = 0;
        for (int i = 0; i < nums.length; i++){
            sum += nums[i];
            if (sum > max){
                max = sum;
            }
            if (sum < 0){
                sum = 0;
            }
        }
        return max;
    }
}
```

### Python

```py
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        max = -sys.maxsize;
        sum = 0;
        for i in range(0, len(nums)):
            sum += nums[i];
            if sum > max:
                max = sum;
            if sum < 0:
                sum = 0

        return max;
```



