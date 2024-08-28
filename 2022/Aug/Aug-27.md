<!-- August-27-->

# LeetCode - [1514. Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/description/)

**Difficulty:** Medium

**Category:**  Dijkstra's Algorithm

---

## Dry Run

<p align="middle">
   <img src="../../Graph/dijkstraAlgorithm.jpg" width="400"/>
</p>

---

## Solution

```java
//Using Dijkstra's Algorithm
//T.C : O(E*log(V))
//S.C : O(V + E)
class Solution {
    public double maxProbability(int n, int[][] edges, double[] succProb, int start, int end) {
        // Build the graph
        Map<Integer, List<Pair<Integer, Double>>> graph = new HashMap<>();
        for (int i = 0; i < edges.length; i++) {
            int u = edges[i][0], v = edges[i][1];
            double pathProb = succProb[i];
            graph.computeIfAbsent(u, k -> new ArrayList<>()).add(new Pair<>(v, pathProb));
            graph.computeIfAbsent(v, k -> new ArrayList<>()).add(new Pair<>(u, pathProb));
        }

        // Array to store the maximum probability to reach each node
        double[] maxProb = new double[n];
        maxProb[start] = 1d;

        // Max-heap priority queue to explore the highest probability first
        PriorityQueue<Pair<Double, Integer>> pq = new PriorityQueue<>((a, b) -> -Double.compare(a.getKey(), b.getKey()));
        pq.add(new Pair<>(1.0, start));

        while (!pq.isEmpty()) {
            Pair<Double, Integer> cur = pq.poll();
            double curProb = cur.getKey();
            int curNode = cur.getValue();

            // If the current node is the end node, return the probability
            if (curNode == end) {
                return curProb;
            }

            // Explore the neighbors
            for (Pair<Integer, Double> nxt : graph.getOrDefault(curNode, new ArrayList<>())) {
                int nxtNode = nxt.getKey();
                double pathProb = nxt.getValue();

                // Update the probability if a higher one is found
                if (curProb * pathProb > maxProb[nxtNode]) {
                    maxProb[nxtNode] = curProb * pathProb;
                    pq.add(new Pair<>(maxProb[nxtNode], nxtNode));
                }
            }
        }

        // If the end node is not reachable, return 0
        return 0d;
    }
}
```
