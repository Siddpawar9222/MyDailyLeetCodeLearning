# LeetCode - [1110. Delete Nodes And Return Forest](https://leetcode.com/problems/delete-nodes-and-return-forest/description/)

**Difficulty:** Medium

**Category:** Tree, DFS

---

## Dry Run

<p align="middle">
   <img src="../../Array/MultiD/1380.jpg" width="400"/>
</p>


---

## Solution

```java
// Approach 1 :
class Solution {
    private TreeNode solve(TreeNode root, Set<Integer> set, List<TreeNode> list) {
        if (root == null) {
            return null;
        }
        root.left = solve(root.left, set, list);
        root.right = solve(root.right, set, list);

        if (set.contains(root.val)) {
            if (root.left != null) {
                list.add(root.left);
            }
            if (root.right != null) {
                list.add(root.right);
            }
            return null;
        }

        return root;
    }

    public List<TreeNode> delNodes(TreeNode root, int[] to_delete) {
        Set<Integer> set = new HashSet<>();
        for (int num : to_delete) {
            set.add(num);
        }
        List<TreeNode> list = new ArrayList<>();

        root = solve(root, set, list);
        if (root != null) {
            list.add(root);
        }
        return list;
    }
}
```
