<!-- Setp 11 -->

# LeetCode - [2220. Minimum Bit Flips to Convert Number](https://leetcode.com/problems/minimum-bit-flips-to-convert-number/description/)

**Difficulty:** Easy

**Category:** Bit Manipulation


---

## Solution

```java
//Brute force
// class Solution {
//     public int minBitFlips(int start, int goal) {
//         int count = 0;
//         for (int bit = 0; bit <= 31; bit++) {
//             count += ((start >> bit) & 1) ^ ((goal >> bit) & 1);
//         }
//         return count;
//     }
// }

class Solution {
    public int minBitFlips(int start, int goal) {
        return Integer.bitCount(start^goal) ;
    }
}
```
