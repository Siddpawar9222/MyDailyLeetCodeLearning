<!-- August-13-->

# LeetCode - [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/description/)

**Difficulty:** Medium

**Category:**  Recursion, Backtracking

**Hint:** Solved on 15 day of 75dayschallenge

---

## Solution

```java
class Solution {
    List<List<Integer>> ans = new ArrayList<>();
    List<Integer> currResult = new ArrayList<>();

    private void solve(int[] nums, int idx, int currSum, int target) {
        int n = nums.length;

        if (currSum == target) {
            ans.add(new ArrayList<>(currResult));
            return;
        }
        if (currSum > target) {
            return;
        }

        for (int i = idx; i < n; i++) {
            if (i > idx && nums[i] == nums[i - 1]) {
                continue;
            }
            if(currSum + nums[i]>target){
                break ;
            }
            currResult.add(nums[i]);
            solve(nums, i + 1, currSum + nums[i], target);
            currResult.remove(currResult.size() - 1);
        }
    }

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        solve(candidates, 0, 0, target);
        return ans;
    }
}
```
