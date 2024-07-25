# LeetCode - [1530. Number of Good Leaf Nodes Pairs](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/description/)

**Difficulty:** Medium

**Category:** Tree, Graph, BFS

---

## Dry Run

<p align="middle">
   <img src="../../Array/MultiD/1380.jpg" width="400"/>
</p>

---

## Solution

```java
class Solution {
        private void buildGraph(TreeNode root, TreeNode prev, Map<TreeNode, List<TreeNode>> adjList, Set<TreeNode> leafNodes) {
        if (root == null) {
            return;
        }

        if (root.left == null && root.right == null) {
            leafNodes.add(root);
        }
        if (prev != null) {
            adjList.computeIfAbsent(root, (k) -> new LinkedList<>()).add(prev);
            adjList.computeIfAbsent(prev, (k) -> new LinkedList<>()).add(root);
        }
        buildGraph(root.left, root, adjList, leafNodes);
        buildGraph(root.right, root, adjList, leafNodes);
    }

    public int countPairs(TreeNode root, int distance) {

        //Convert tree to graph
        Map<TreeNode, List<TreeNode>> adjList = new HashMap<>();
        Set<TreeNode> leafNodes = new HashSet<>();
        buildGraph(root, null, adjList, leafNodes);
        int count = 0;

        // performing bfs
        for (TreeNode leaf : leafNodes) {
            Queue<TreeNode> queue = new LinkedList<>();
            Set<TreeNode> visitedNode = new HashSet<>();
            queue.offer(leaf);
            visitedNode.add(leaf);

            for (int level = 0; level <= distance; level++) {
                int size = queue.size();

                while (size != 0) {
                    TreeNode currNode = queue.poll();
                    if (leafNodes.contains(currNode) && !Objects.equals(currNode, leaf)) {
                        count++;
                    }
                    for (TreeNode neigb : adjList.getOrDefault(currNode, new LinkedList<>())) {
                        if (!visitedNode.contains(neigb)) {
                            visitedNode.add(neigb);
                            queue.offer(neigb);
                        }
                    }
                    size--;
                }

            }
        }

        return count / 2;
    }
}
```
