<!-- July 6 -->

# LeetCode - [2582. Pass the Pillow](https://leetcode.com/problems/pass-the-pillow/description/)

**Difficulty:** Easy

**Category:** Array, Math

---

## Solution

```java
class Solution {
   // Simulation
//    public int passThePillow(int n, int time) {
//        int idx = 1 ;
//        int dir =1 ;
//        while(time!=0){
//             if(idx+dir<=n && idx+dir>=1){
//                  time -- ;
//                  idx += dir ;
//             }else{
//                  dir *= -1 ;
//             }
//        }
//        return idx ;
//     }

    // Derived Formula
       public int passThePillow(int n, int time) {
        int passes = n-1 ; //number of time pillow passes for 1 to n
        int totalFullRounds = time / passes;
        int timeLeft = time % passes;

        if (totalFullRounds % 2 == 0) {
            return timeLeft + 1;
        } else {
            return n - timeLeft;
        }
    }
}
```

---

<!-- July 7 -->

# LeetCode - [1518. Water Bottles](https://leetcode.com/problems/water-bottles/description/)

**Difficulty:** Easy

**Category:** Math

---

## Solution

```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int emptyBottles = 0;
        int ans = 0;

        while (numBottles != 0) {
            ans += numBottles;
            emptyBottles += numBottles;
            if (emptyBottles < numExchange) {
                return ans;
            }
            numBottles = emptyBottles / numExchange;
            emptyBottles = emptyBottles % numExchange;
        }

        return ans;
    }
}
```

---

<!-- July 8 -->

# LeetCode - [1823. Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/)

**Difficulty:** Medium

**Category:** Math, LinkedList

---

## Solution

```java
class Solution {
    public int findTheWinner(int n, int k) {
        if (n == 1) {
            return n;
        }
        List<Integer> list = new LinkedList<>();

        for (int i = 1; i <= n; i++) {
            list.add(i);
        }

        int count = 0;
        int idx = 0;
        while (list.size() != 1) {
            count++;
            if (count == k) {
                list.remove(idx);
                count = 0;
            } else {
                idx++;
            }
            if (idx == list.size()) {
                idx = 0;
            }
        }
        return list.get(0);
    }
}
```

---

<!-- July 9-->

# LeetCode - [1701. Average Waiting Time](https://leetcode.com/problems/average-waiting-time/description/)

**Difficulty:** Medium

**Category:** Array, Math

---

## Solution

```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        double sum = 0;
        int freeAt = -1;
        int n = customers.length ;
        for (int i = 0; i < n; i++) {
            int arrivalT = customers[i][0];
            int time = customers[i][1];
            if (arrivalT < freeAt) {
                sum += freeAt + time - arrivalT;
                freeAt = freeAt + time;
            } else {
                sum += arrivalT + time - arrivalT;
                freeAt = arrivalT + time;
            }

        }
        return (double)sum/n;
    }
}
```
