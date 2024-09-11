<!-- Setp 10 -->

# LeetCode - [2807. Insert Greatest Common Divisors in Linked List](https://leetcode.com/problems/insert-greatest-common-divisors-in-linked-list/description/)

**Difficulty:** Medium

**Category:** Linked List


---

## Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 * int val;
 * ListNode next;
 * ListNode() {}
 * ListNode(int val) { this.val = val; }
 * ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    private int calculateGCD(int a, int b) {
        if (b == 0) {
            return a;
        }
        return calculateGCD(b, a % b);
    }

    public ListNode insertGreatestCommonDivisors(ListNode head) {
        if (head == null || head.next == null) {
            return head; // Edge case: if there's only one node, return it
        }

        ListNode prev = head; // Start with the first node
        ListNode curr = head.next; // Second node
        ListNode ans = new ListNode(prev.val); // Initialize result list with the first node
        ListNode result = ans; // Pointer to the start of the new list

        while (curr != null) {
            // Calculate GCD of adjacent nodes
            int gcdVal = this.calculateGCD(prev.val, curr.val);

            // Add GCD node to the result list
            result.next = new ListNode(gcdVal);
            result = result.next;

            // Add the current node to the result list
            result.next = new ListNode(curr.val);
            result = result.next;

            // Move the pointers forward
            prev = curr;
            curr = curr.next;
        }

        return ans; // Return the new head of the list
    }
}

```
