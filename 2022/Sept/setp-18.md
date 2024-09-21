<!-- Setp 18 -->

# LeetCode - [179. Largest Number](https://leetcode.com/problems/largest-number/description/)

**Difficulty:** Medium

**Category:** Arrays, Comparators


---

## Solution

```java
   class Solution {
    public String largestNumber(int[] nums) {
        int n = nums.length;
        String[] temp = new String[n];
        for (int i = 0; i < n; i++) {
            temp[i] = String.valueOf(nums[i]);
        }

        Arrays.sort(temp, (a, b) -> {
            String order1 = a + b;
            String order2 = b + a;

            // Use if-else to compare the concatenated results
            // if (order1.compareTo(order2) < 0) {
            //     return 1; // Means b should come before a
            // } else if (order1.compareTo(order2) > 0) {
            //     return -1; // Means a should come before b
            // } else {
            //     return 0; // Means they are equal
            // }

            return order2.compareTo(order1);
        });

        if (temp[0].equals("0")) {
            return "0";
        }

        StringBuilder ans = new StringBuilder();
        for (String num : temp) {
            ans.append(num);
        }

        return ans.toString();
    }
}
```
