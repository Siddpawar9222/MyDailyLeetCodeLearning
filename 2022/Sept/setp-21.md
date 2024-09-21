<!-- Setp 21 -->

# LeetCode - [386. Lexicographical Numbers](https://leetcode.com/problems/lexicographical-numbers/description/)

**Difficulty:** Medium

**Category:** Arrays, Comparators


---

## Solution

```java
   class Solution {
    public List<Integer> lexicalOrder(int n) {
        String[] temp = new String[n + 1];
        temp[0] = "0";
        for (int i = 1; i <= n; i++) {
            temp[i] = String.valueOf(i);
        }

        Arrays.sort(temp, (a, b) -> {
            if (a.compareTo(b) > 0) {
                return 1;
            } else if (a.compareTo(b) < 0) {
                return -1;
            } else {
                return 0;
            }
        });

        List<Integer> ans = new ArrayList<>();
        for (int i = 1; i <= n; i++) {
            ans.add(Integer.parseInt(temp[i]));
        }
        return ans;
    }
}
```
