<!-- August-25 -->

# LeetCode - [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)

**Difficulty:** Easy

**Category:**  Binary Tree

---
Note : 

PreOrder : root, left, right

InOrder : left, root, right

PostOrder : left, right, root

---

## Solution

```java
class Solution {
    private void solve(TreeNode root, List<Integer> ans) {
        if (root == null) {
            return;
        }
        solve(root.left, ans);
        solve(root.right, ans);
        ans.add(root.val);
    }

    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        this.solve(root, ans);
        return ans;
    }
}
```
