<!-- July 4 -->

# LeetCode - [2181. Merge Nodes in Between Zeros](https://leetcode.com/problems/merge-nodes-in-between-zeros/description/)

**Difficulty:** Medium

**Category:** LinkedList

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
    //Brute Force Approach
    // public ListNode mergeNodes(ListNode head) {
    //     ListNode ans = new ListNode(-1);
    //     ListNode ref = ans;

    //     ListNode currNode = head;
    //     int sum = 0;
    //     while (currNode.next != null) {
    //         int val = currNode.next.val;
    //         if (val != 0) {
    //             sum += val;
    //             currNode = currNode.next;
    //         } else {
    //             ListNode newNode = new ListNode(sum);
    //             ref.next = newNode;
    //             ref = ref.next;
    //             currNode = currNode.next;
    //             sum = 0;
    //         }
    //     }
    //     return ans.next;
    // }

    // Optimum  Solution
       public ListNode mergeNodes(ListNode head) {
        ListNode p1 = head.next;
        ListNode p2 = head.next;
        int sum =0;
        while (p1!=null && p2!=null){
            if(p2.val!=0){
                sum+= p2.val;
                p2 =p2.next;
            }else{
                ListNode temp = p2.next;
                p1.val = sum ;
                p1.next = p2.next ;
                p1 =temp ;
                p2 =temp ;
                sum =0 ;
            }
        }
        return head.next ;
    }
}
```

---

<!-- July 5 -->

# LeetCode - [2058. Find the Minimum and Maximum Number of Nodes Between Critical Points](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/)

**Difficulty:** Medium

**Category:** LinkedList

---

## Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
      // with O(n) space complicity
    //     public int[] nodesBetweenCriticalPoints(ListNode head) {
    //    List<Integer> cp = new ArrayList<>();

    //    ListNode prev = null ;
    //    ListNode currNode = head ;
    //    int position=1 ;
    //    while(currNode!=null){
    //        ListNode nextNode = currNode.next ;
    //        if(prev!=null && nextNode!=null){
    //            if(currNode.val< prev.val && currNode.val<nextNode.val){
    //                cp.add(position);
    //            }
    //            if(currNode.val> prev.val && currNode.val>nextNode.val){
    //                cp.add(position);
    //            }
    //        }
    //        prev = currNode ;
    //        currNode = nextNode ;
    //        position++ ;
    //    }
    //    if(cp.size()<2){
    //        return new int[]{-1,-1};
    //    }

    //    int minDistance = Integer.MAX_VALUE;
    //    int maxDistance = cp.get(cp.size()-1) - cp.get(0);

    //     for (int i = 1; i < cp.size() ; i++) {
    //          minDistance = Math.min(minDistance,cp.get(i)- cp.get(i-1));
    //     }
    //    return new int[]{minDistance,maxDistance};
    // }


     //O(1) space
     public int[] nodesBetweenCriticalPoints(ListNode head) {
       ListNode prev = null ;
       ListNode currNode = head ;
       int startcp =-1 ;
       int endcp=-1 ;
       int position=1 ;
        int minDistance = Integer.MAX_VALUE;
       while(currNode!=null){
           ListNode nextNode = currNode.next ;
           if(prev!=null && nextNode!=null){
               if(currNode.val< prev.val && currNode.val<nextNode.val ||
                       currNode.val> prev.val && currNode.val>nextNode.val){
                    if(startcp==-1){
                         startcp = position ;
                    }else{
                        minDistance = Math.min(minDistance,position-endcp);
                    }
                   endcp = position ;
               }
           }
           prev = currNode ;
           currNode = nextNode ;
           position++ ;
       }
        if (startcp == -1 || startcp == endcp) {
            return new int[] {-1, -1};
        }

        return new int[] {minDistance, endcp - startcp};
    }
}
```
