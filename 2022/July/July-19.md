# LeetCode - [1380. Lucky Numbers in a Matrix](https://leetcode.com/problems/lucky-numbers-in-a-matrix/description/)

**Difficulty:** Easy

**Category:** Multi-dimensional Arrays, Greedy

---

## Dry Run

<p align="middle">
   <img src="../../Array/MultiD/1380.jpg" width="400"/>
</p>


---

## Solution

```java
// Brute Force Approach
// class Solution {
//     public List<Integer> luckyNumbers(int[][] matrix) {
//         List<Integer> ans = new ArrayList<>();
//         Set<Integer> minRow = new HashSet<>();
//         Set<Integer> maxCol = new HashSet<>();

//         // Take row
//         for (int[] row : matrix) {
//             int min = Integer.MAX_VALUE;
//             for (int num : row) {
//                 min = Math.min(min, num);
//             }
//             minRow.add(min);
//         }

//         // Take col
//         for (int j = 0; j < matrix[0].length; j++) {
//             int max = Integer.MIN_VALUE;
//             for (int i = 0; i < matrix.length; i++) {
//                 max = Math.max(max, matrix[i][j]);
//             }
//             maxCol.add(max);
//         }

//         for (int num : minRow) {
//             if (maxCol.contains(num)) {
//                 ans.add(num);
//                 break ;
//             }
//         }

//         return ans;
//     }
// }

// Optimal Solution : 1
// class Solution {
//     public List<Integer> luckyNumbers(int[][] matrix) {

//         int[] r = new int[matrix.length];
//         int[] c = new int[matrix[0].length];

//         for (int i = 0; i < matrix.length; i++) {
//             int min = Integer.MAX_VALUE;
//             for (int j = 0; j < matrix[0].length; j++) {
//                 min = Math.min(min, matrix[i][j]);
//             }
//             r[i] = min;
//         }

//         for (int i = 0; i < matrix[0].length; i++) {
//             int max = Integer.MIN_VALUE;
//             for (int j = 0; j < matrix.length; j++) {
//                 max = Math.max(max, matrix[j][i]);
//             }
//             c[i] = max;
//         }

//         for (int i = 0; i < matrix.length; i++) {
//             for (int j = 0; j < matrix[0].length; j++) {
//                 if (r[i] == c[j]) {
//                     return List.of(matrix[i][j]);
//                 }
//             }
//         }
//         return List.of();
//     }
// }


//Optimal Solution : 2
class Solution {
    public List<Integer> luckyNumbers(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;

        for (int i = 0; i < m; i++) {
            int rowMin = Integer.MAX_VALUE;
            int colMaxInd = -1;
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] < rowMin) {
                    rowMin = matrix[i][j];
                    colMaxInd = j;
                }
            }
            boolean flag = false;
            for (int k = 0; k < m; k++) {
                if (matrix[k][colMaxInd] > rowMin) {
                    flag = true;
                    break;
                }
            }

            if (!flag) {
                return List.of(rowMin);
            }
        }
        return List.of();
    }
}
```
