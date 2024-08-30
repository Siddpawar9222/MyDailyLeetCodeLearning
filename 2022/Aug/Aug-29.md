<!-- August-29-->

# LeetCode - [947. Most Stones Removed with Same Row or Column](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/description/)

**Difficulty:** Medium

**Category:**  DFS

---

## Dry Run

<p align="middle">
   <img src="../../Graph/dijkstraAlgorithm.jpg" width="400"/>
</p>

---

## Solution

```java
class Solution {
    public int removeStones(int[][] stones) {
        boolean[] visited = new boolean[stones.length];
        HashMap<Integer, List<Integer>> row = new HashMap<>();
        HashMap<Integer, List<Integer>> col = new HashMap<>();
        for (int i = 0; i < stones.length; i++){
            row.computeIfAbsent(stones[i][0], o -> new ArrayList<>()).add(i); // so we can find other stones based on row
            col.computeIfAbsent(stones[i][1], o -> new ArrayList<>()).add(i); // so we can find other stones based on col
        }

        int numOfIsland = 0;
        for (int i = 0; i < stones.length; i++)
            if (!visited[i]){
                removeIsland(visited, stones, i, row, col);
                numOfIsland++;
            }

        return stones.length - numOfIsland;
    }

    private void removeIsland(boolean[] visited, int[][] stones, int idx,
                              Map<Integer, List<Integer>> row, Map<Integer, List<Integer>> col){
        if (visited[idx]) return; // base case

        visited[idx] = true; // mark as visited.
        int r = stones[idx][0];
        int c = stones[idx][1];
        for (int index : row.get(r)) // not null because the current stone is in it
            removeIsland(visited, stones, index, row, col); // visit all the stones on this row

        for (int index : col.get(c))
            removeIsland(visited, stones, index, row, col); // visit all the stones on this col
    }
}

```
