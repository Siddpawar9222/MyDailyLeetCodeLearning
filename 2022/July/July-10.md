<!-- July 10 -->

# LeetCode - [1598. Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)

**Difficulty:** Easy

**Category:** Stack

---

## Solution

```java
class Solution {
    public int minOperations(String[] logs) {
        Stack<String> dir = new Stack<>();
        for(String log : logs){
            if(!dir.isEmpty() && log.equals("../")){
                 dir.pop();
            }
            if(!log.equals("../") && !log.equals("./")){
                 dir.push(log);
            }
        }

        return  dir.size();
    }
}
class Solution {
    public int minOperations(String[] logs) {
        int ans = 0 ;
        for(String log : logs){
            if(ans!=0 && log.equals("../")){
                 ans--;
            }
            if(!log.equals("../") && !log.equals("./")){
                 ans ++ ;
            }
        }
        return  ans ;
    }
}
```
