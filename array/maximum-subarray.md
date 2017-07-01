# Maximum Subarray

> Find the contiguous subarray within an array \(containing at least one number\) which has the largest sum.
>
> For example, given the array`[-2,1,-3,4,-1,2,1,-5,4]`,  
> the contiguous subarray`[4,-1,2,1]`has the largest sum =`6`.

原题链接：[https://leetcode.com/problems/maximum-subarray/\#/description](https://leetcode.com/problems/maximum-subarray/#/description)

## 题意

## 解析

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

### Python



