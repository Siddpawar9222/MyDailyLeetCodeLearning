<!-- setp-1 -->

# LeetCode - [2022. Convert 1D Array Into 2D Array](https://leetcode.com/problems/convert-1d-array-into-2d-array/description/)

**Difficulty:** Easy

**Category:** Arrays, 2D Arrays

---


---

## Solution

```java
// Brute Force

// class Solution {
//     public int[][] construct2DArray(int[] original, int m, int n) {
//         int size = original.length;
//         if (size > m * n || m * n > size) {
//             return new int[][] {};
//         }
//         int[][] ans = new int[m][n];

//         int r = 0;
//         int c = 0;
//         int idx = 0;
//         while (r < m) {
//             ans[r][c] = original[idx];
//             idx++;
//             c++;
//             if (c == n) {
//                 c = 0;
//                 r++;
//             }
//         }
//         return ans;
//     }
// }


//Arranged program
class Solution {
    public int[][] construct2DArray(int[] original, int m, int n) {
        int size = original.length;

        // Check if it's possible m*n>size or size>m*n
        if (size != m * n) {
            return new int[][] {};
        }

        int[][] ans = new int[m][n];
        int idx = 0;

        // Fill the 2D array row by row
        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                ans[r][c] = original[idx++];
            }
        }

        return ans;
    }
}
```
