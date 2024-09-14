<!-- Setp 12 -->

# LeetCode - [1684. Count the Number of Consistent Strings](https://leetcode.com/problems/count-the-number-of-consistent-strings/description/)

**Difficulty:** Easy

**Category:** String


---

## Solution

```java
    class Solution {
    public int countConsistentStrings(String allowed, String[] words) {
        int count = 0;
        Set<Character> allowedSet =  new HashSet<>();
        for(char ch : allowed.toCharArray()){
            allowedSet.add(ch);
        }

        for(String word : words) {
            boolean flag = true ;
            for (char ch : word.toCharArray()) {
                if (!allowedSet.contains(ch)) {
                    flag = false;
                    break;
                }
            }
            count +=  flag ? 1 : 0;
        }
        return count;
    }
}
```
