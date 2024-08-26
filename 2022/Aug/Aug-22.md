<!-- August-22-->

# LeetCode - [476. Number Complement](https://leetcode.com/problems/number-complement/description/)

**Difficulty:** Easy

**Category:**  String

---

## Dry Run

<p align="middle">
   <img src="../../String/476.jpg" width="400"/>
</p>

---

## Solution

```java
class Solution {
    private String numberToString(int num) {
        StringBuilder sb = new StringBuilder("");
        int temp = num;

        while (temp > 0) {
            int rem = temp % 2;
            sb.insert(0, rem);
            temp /= 2;
        }

        while (sb.length() > 0 && sb.charAt(0) != '1') {
            sb.deleteCharAt(0);
        }

        return sb.toString();
    }

    public int findComplement(int num) {
        String binaryNum = this.numberToString(num);

        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < binaryNum.length(); i++) {
            sb.append(binaryNum.charAt(i) == '1' ? '0' : '1');
        }

        int ans = 0;
        int idx = 0;

        for (int i = sb.length() - 1; i >= 0; i--) {
            ans += (sb.charAt(i) - '0') * (int) Math.pow(2, idx);
            idx++;
        }

        return ans;
    }
}
```
