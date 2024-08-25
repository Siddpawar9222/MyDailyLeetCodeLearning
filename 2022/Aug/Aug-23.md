<!-- August-23-->

# LeetCode - [592. Fraction Addition and Subtraction](https://leetcode.com/problems/fraction-addition-and-subtraction/description/)

**Difficulty:** Medium

**Category:**  String, Simulation

---

## Dry Run

<p align="middle">
   <img src="../../String/592.jpg" width="400"/>
</p>

---

## Solution

```java
//Using Recursion
class Solution {
    private int solve(int n ,int currA, int clipB){
        if(currA==n){
            return 0 ;
        }

        if(currA>n){
            return 1001;
        }

        int copyAndPaste = 1 + 1 + solve(n, currA + currA,currA);
        int paste = 1 + solve(n, currA+clipB,clipB);

        return Math.min(copyAndPaste,paste);
    }
    public int minSteps(int n) {
        if(n==1){
            return 0 ;
        }
        int result = 1 + solve(n,1,1);
        return result;
    }
}
```
