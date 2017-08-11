# Climbing Stairs

> You are climbing a stair case. It takes `n` steps to reach to the top.
>
> Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
>
> **Note: **Givennwill be a positive integer.

原题链接：[https://leetcode.com/problems/climbing-stairs/\#/description](https://leetcode.com/problems/climbing-stairs/#/description)

## 题意

`n` 级楼梯，每次只能走 1 级或 2 级，问有多少种情况？

## 解析

这一题乍一看似乎情况有点复杂，但如果从后往前推，会发现最后一次要么只剩一级，要么只剩两级，那情况的总数为 `f(n-1) + f(n-2)`，即我们耳熟能详的斐波那契数列。

## 代码

### C++

```cpp
class Solution {
public:
    int climbStairs(int n) {
        int f1 = 1, f2 = 2, f3 = 0;
        if (n == 1){
            return 1;
        }
        else if (n == 2){
            return 2;
        }
        for (int i = 2; i < n; i++){
            f3 = f1 + f2;
            f1 = f2;
            f2 = f3;
        }
        return f3;
    }
};
```

### Java

```java
public class Solution {
    public int climbStairs(int n) {
        int f1 = 1, f2 = 2, f3 = 0;
        if (n == 1){
            return 1;
        }
        else if (n == 2){
            return 2;
        }
        for (int i = 2; i < n; i++){
            f3 = f1 + f2;
            f1 = f2;
            f2 = f3;
        }
        return f3;

    }
}
```

### Python

```py
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        f1 = 1;
        f2 = 2;
        f3 = 0;
        if n == 1:
            return 1;
        elif n == 2:
            return 2;
        for i in range(2, n):
            f3 = f1 + f2;
            f1 = f2;
            f2 = f3;

        return f3;
```



