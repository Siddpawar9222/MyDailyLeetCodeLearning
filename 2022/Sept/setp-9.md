<!-- Setp 9 -->

# LeetCode - [2326. Spiral Matrix IV](https://leetcode.com/problems/spiral-matrix-iv/description/)

**Difficulty:** Medium

**Category:** Linked List,2D Matrix


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

//Brute force Approach
// class Solution {
//     public int[][] spiralMatrix(int m, int n, ListNode head) {
//         int[][] ans = new int[m][n];

//         // Fill whole array with -1
//         for (int[] row : ans) {
//             Arrays.fill(row, -1);
//         }

//         int i = 0;
//         int j = 0;
//         int l = 0;
//         int t = 0;
//         int r = n - 1;
//         int b = m - 1;

//         ListNode ref = head;

//         while (l <= r && t <= b && ref != null) {

//             // Move to right
//             while (j <= r && l <= r && ref != null) {
//                 ans[i][j] = ref.val;
//                 j++;
//                 ref = ref.next;
//             }
//             j--;
//             i++;
//             t++;

//             // Move to bottom

//             while (i <= b && t <= b && ref != null) {
//                 ans[i][j] = ref.val;
//                 i++;
//                 ref = ref.next;
//             }
//             i--;
//             j--;
//             r--;

//             // Move to left

//             while (j >= l && l <= r && ref != null) {
//                 ans[i][j] = ref.val;
//                 j--;
//                 ref = ref.next;
//             }
//             i--;
//             j++;
//             b--;
//             // Move to top

//             while (i >= t && t <= b && ref != null) {
//                 ans[i][j] = ref.val;
//                 i--;
//                 ref = ref.next;
//             }
//             i++;
//             j++;
//             l++;

//         }

//         return ans;
//     }
// }

//Optimium Approach (Better Structure)

class Solution {
    public int[][] spiralMatrix(int m, int n, ListNode head) {
        int[][] spiral= new int[m][n];
        for(int i = 0; i < m; i++){
            Arrays.fill(spiral[i], -1);
        }
        int topR = 0, btmR = m-1, lftC = 0, rytC = n-1;
        while(head!=null){
            //Fill Top Row
            for(int col = lftC; col <= rytC && head != null; col++){
                spiral[topR][col] = head.val;
                head = head.next;
            }
            topR++;
            //Fill Right Column
            for(int row = topR; row <= btmR && head != null; row++){
                spiral[row][rytC] = head.val;
                head = head.next;
            }
            rytC--;
            //Fill Bottom Row
            for(int col = rytC; col >= lftC && head != null; col--){
                spiral[btmR][col] = head.val;
                head = head.next;
            }
            btmR--;
            //Fill Left Column
            for(int row = btmR; row >= topR && head != null; row--){
                spiral[row][lftC] = head.val;
                head = head.next;
            }
            lftC++;
        }
        return spiral;
    }
}
```
