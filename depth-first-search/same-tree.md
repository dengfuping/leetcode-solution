# Same Tree

> Given two binary trees, write a function to check if they are equal or not.
>
> Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

原题链接：[https://leetcode.com/problems/same-tree/\#/description](https://leetcode.com/problems/same-tree/#/description)

## 题意

判断两棵二叉树是否相同，包括树的结构和各个节点值。

## 解析

这题太简单了，就不分析了，直接看代码吧。

## 代码

### C++

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (p == nullptr && q == nullptr){
            return true;
        }
        else if (p == nullptr && q != nullptr){
            return false;
        }
        else if (p != nullptr && q == nullptr){
            return false;
        }
        else if (p->val != q->val){
            return false;
        }
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```

### Java

```java

```

### Python

```py

```



