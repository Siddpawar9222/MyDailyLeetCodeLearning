<!-- Setp 25 -->

# LeetCode - [440. K-th Smallest in Lexicographical Order](https://leetcode.com/problems/k-th-smallest-in-lexicographical-order/)

**Difficulty:** Medium

**Category:** Arrays, Comparators

---

## Solution

```java
//Gave TLE
// class Solution {
//     public int findKthNumber(int n, int k) {
//         String[] temp = new String[n + 1];
//         temp[0] = "0";
//         for (int i = 1; i <= n; i++) {
//             temp[i] = String.valueOf(i);
//         }

//         Arrays.sort(temp, (a, b) -> {
//             if (a.compareTo(b) > 0) {
//                 return 1;
//             } else if (a.compareTo(b) < 0) {
//                 return -1;
//             } else {
//                 return 0;
//             }
//         });

//         int ans = -1;

//         for (int i = 0; i <= k; i++) {
//             ans = Integer.parseInt(temp[i]);
//         }

//         return ans;
//     }
// }

//More Optimised 
// Learn this solution later
class Solution {
    public int findKthNumber(int n, int k) {
        int current = 1;
        k--;

        while (k > 0) {
            int count = countPrefix(current, n);
            if (count <= k) {
                current++;
                k -= count;
            } else {
                current *= 10;
                k--;
            }
        }
        return current;
    }

    private int countPrefix(int prefix, int n) {
        long curr = prefix;
        long next = prefix + 1;
        int count = 0;

        while (curr <= n) {
            count += Math.min(n + 1, next) - curr;
            curr *= 10;
            next *= 10;
        }
        return count;
    }
}
```
