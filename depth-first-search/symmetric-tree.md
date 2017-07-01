# Symmetric Tree

> Given a binary tree, check whether it is a mirror of itself \(ie, symmetric around its center\).
>
> For example, this binary tree`[1,2,2,3,4,4,3]`is symmetric:
>
> ```
>     1
>    / \
>   2   2
>  / \ / \
> 3  4 4  3
> ```
>
> But the following`[1,2,2,null,3,null,3]`is not:
>
> ```
>     1
>    / \
>   2   2
>    \   \
>    3    3
> ```

原题链接：[https://leetcode.com/problems/symmetric-tree/\#/description](https://leetcode.com/problems/symmetric-tree/#/description)

## 题意

判断一棵树是否是对称树（轴对称）。

## 解析

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
    bool isSymmetricTree(TreeNode* p, TreeNode* q){
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
        return isSymmetricTree(p->left, q->right) && isSymmetricTree(p->right, q->left);
    }

    bool isSymmetric(TreeNode* root) {
        if (root == nullptr){
            return true;
        }
        return isSymmetricTree(root->left, root->right);
    }
};
```

### Java

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public boolean isSymmetricTree(TreeNode p, TreeNode q){
        if (p == null && q == null){
            return true;
        }
        else if (p == null && q != null){
            return false;
        }
        else if (p != null && q == null){
            return false;
        }
        else if (p.val != q.val){
            return false;
        }
        return isSymmetricTree(p.left, q.right) && isSymmetricTree(p.right, q.left);
    }
    
    public boolean isSymmetric(TreeNode root) {
        if (root == null){
            return true;
        }
        return isSymmetricTree(root.left, root.right);
    }
}
```

### Python

```py

```



