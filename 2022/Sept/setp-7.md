<!-- setp-7 -->

# LeetCode - [1367. Linked List in Binary Tree](https://leetcode.com/problems/linked-list-in-binary-tree/description/)

**Difficulty:** Medium

**Category:** Linked List, Binary Tree


---

## Solution

```java
class Solution {
    private boolean solve(List<Integer> list, TreeNode root, int idx) {
        if (idx == list.size()) {  // If the entire list is matched
            return true;
        }
        if (root == null) {  // If the tree path ends without matching the list
            return false;
        }
        if (root.val == list.get(idx)) {  // If the current node matches the list element
            // Try to match the rest of the list down the left or right subtree
            return solve(list, root.left, idx + 1) || solve(list, root.right, idx + 1);
        }
        // If the current node doesn't match, return false without restarting
        return false;
    }

    public boolean isSubPath(ListNode head, TreeNode root) {
        List<Integer> list = new ArrayList<>();
        ListNode curr = head;
        while (curr != null) {
            list.add(curr.val);
            curr = curr.next;
        }
        return checkPath(list, root);
    }
    
    private boolean checkPath(List<Integer> list, TreeNode root) {
        if (root == null) {
            return false;
        }
        // Check if we can start matching the list from the current node,
        // or try matching from the left and right children.
        return solve(list, root, 0) || checkPath(list, root.left) || checkPath(list, root.right);
    }
}
```
