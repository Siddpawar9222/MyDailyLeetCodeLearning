<!-- Setp 6 -->

# LeetCode - [3217. Delete Nodes From Linked List Present in Array](https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/description/)

**Difficulty:** Medium

**Category:** Linked List

---

## Dry Run

<p align="middle">
   <img src="../../DP/1105.jpg" width="400"/>
 <img src="../../DP/1105_1.jpg" width="400"/>
</p>

---

## Solution

```java
class Solution {
    public ListNode modifiedList(int[] nums, ListNode head) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }
        ListNode ref = new ListNode(-1);
        ref.next = head;

        ListNode prev = ref;
        ListNode curr = head;
        while (curr != null) {
            if (set.contains(curr.val)) {
                prev.next = curr.next;
                curr = curr.next;
            } else {
                prev = curr;
                curr = curr.next;
            }
        }

        return ref.next;
    }
}
```
