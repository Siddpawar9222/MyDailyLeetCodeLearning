<!-- Setp 30 -->

# LeetCode - [1381. Design a Stack With Increment Operation](https://leetcode.com/problems/design-a-stack-with-increment-operation/description/)

**Difficulty:** Medium

**Category:** Stack, Arrays

---

## Solution

```java
class CustomStack {
    int[] stack;
    int idx = -1;

    public CustomStack(int maxSize) {
        stack = new int[maxSize];
    }

    public void push(int x) {
        if (idx < stack.length - 1) {
            stack[idx + 1] = x;
            idx++;
        }
    }

    public int pop() {
        if (idx != -1) {
            int topElement = stack[idx];
            stack[idx] = 0;
            idx--;
            return topElement;
        }
        return -1;
    }

    public void increment(int k, int val) {
        for (int i = 0; i < k && i < idx + 1; i++) {
            stack[i] = stack[i] + val;
        }
    }
}
```
