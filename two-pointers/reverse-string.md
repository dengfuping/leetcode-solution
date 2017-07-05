# Reverse String

> Write a function that takes a string as input and returns the string reversed.

原题链接：[https://leetcode.com/problems/reverse-string/\#/description](https://leetcode.com/problems/reverse-string/#/description)

## 题意

将所给字符串进行逆置。

## 解析

将字符串元素进行头尾交换，即第一个和倒数第一个交换，第二个和倒数第二个......进行交换。

## 代码

### C++

```cpp
class Solution {
public:
    string reverseString(string s) {
        int length = s.length();
        int i = 0;
        int j = length - 1;
        while (i < j){
            swap(s[i], s[j]);
            i++;
            j--;
        }
        return s;
    }
};
```



