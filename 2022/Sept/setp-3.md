<!-- sept 3 -->

# LeetCode - [1945. Sum of Digits of String After Convert](https://leetcode.com/problems/sum-of-digits-of-string-after-convert/)

**Difficulty:** Easy

**Category:** String, Simulation

---


## Solution

```java
//Brute force
// class Solution {
//         public int getLucky(String s, int k) {

//             while (k != 0) {
//                 StringBuilder sb = new StringBuilder();
//                 for (char ch : s.toCharArray()) {
//                     int temp = Character.isAlphabetic(ch) ? ch - 97 + 1 : ch - 48;
//                     sb.append(temp);
//                 }
//                 int result = 0;
//                 for (int i = 0; i < sb.length(); i++) {
//                     char ch = sb.charAt(i);
//                     result += ch - 48;
//                 }

//                 s = String.valueOf(result);
//                 k--;
//             }
//             return Integer.parseInt(s);
//         }
// }

//Optimised
class Solution {
    public int getLucky(String s, int k) {
        int num = 0;
        for (char c : s.toCharArray()) {
            int temp = c - 'a' + 1;
            while (temp > 0) {
                num += temp % 10;
                temp /= 10;
            }
        }
        k -= 1;
        for (int i = 0 ; i < k ; i++) {
            int sum = 0;
            while (num > 0) {
                sum += num % 10;
                num /= 10;
            }
            num = sum;
        }
        return num;
    }
}
```
