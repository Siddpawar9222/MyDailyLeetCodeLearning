<!-- August-16-->

# LeetCode - [624. Maximum Distance in Arrays](https://leetcode.com/problems/maximum-distance-in-arrays/description/)

**Difficulty:**Medium

**Category:**  Array


---

## Dry Run

<p align="middle">
   <img src="../../Heap/703.jpg" width="400"/>
</p>

---

## Solution

```java

class KthLargest {
    private final int k;
    private final Queue<Integer> queue;   //min-heap

    public KthLargest(int k, int[] nums) {
        this.k = k;
        this.queue = new PriorityQueue<>();
        for (int num : nums) {
            add(num);
        }
    }

    public int add(int val) {
        queue.offer(val);
        if (queue.size() > k) {
            queue.poll();
        }
        return queue.peek();
    }
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest obj = new KthLargest(k, nums);
 * int param_1 = obj.add(val);
 */
```
