# Remove Duplicates from Sorted Array

> Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.
>
> Do not allocate extra space for another array, you must do this in place with constant memory.
>
> For example,  
> Given input arraynums=`[1,1,2]`,
>
> Your function should return length =`2`, with the first two elements ofnumsbeing`1`and`2`respectively. It doesn't matter what you leave beyond the new length.

原题链接：[https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

## 题意

已排序数组去重，要求不能分配额外空间（即只能在原数组上进行操作），并且返回去重后数组的长度。

## 解析

非常典型的`双指针`应用场景，解法见代码。

## 代码

### C++

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() == 0){
            return 0;
        }
        int j = 0;
        for (int i = 1; i < nums.size(); i++){
            if (nums[j] != nums[i]){
                j++;
                nums[j] = nums[i];
            }
        }

        return j + 1;
    }
};
```

### Java

```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0){
            return 0;
        }
        int j = 0;
        for (int i = 1; i < nums.length; i++){
            if (nums[j] != nums[i]){
                j++;
                nums[j] = nums[i];
            }
        }

        return j + 1;
    }
}
```

### Python

```py
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 0:
            return 0;
        j = 0;
        for i in range(1, len(nums)):
            if nums[j] != nums[i]:
                j = j + 1;
                nums[j] = nums[i];
        
        return j + 1;
```



