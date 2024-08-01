# LeetCode - [1550]()

**Difficulty:** Easy

**Category:** Array

---

## Dry Run

[//]: # (<p align="middle">)

[//]: # (   <img src="../../Array/MultiD/1380.jpg" width="400"/>)

[//]: # (</p>)

---

## Solution

```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
       int n = arr.length ;
       if(n<3){
         return false ;
       } 

       for(int i=0 ;i<n-2 ;i++){
             if(arr[i]%2!=0 && arr[i+1]%2!=0 && arr[i+2]%2!=0){
                  return true ;
             }
        }

       return false ;
    }
}


```
# LeetCode - [350]()

**Difficulty:** Easy

**Category:** Array, HashMap

---

## Dry Run

[//]: # (<p align="middle">)

[//]: # (   <img src="../../Array/MultiD/1380.jpg" width="400"/>)

[//]: # (</p>)

---

## Solution

```java
class Solution {
        public int[] intersect(int[] nums1, int[] nums2) {
        Map<Integer,Integer> num1Map = new HashMap<>();
        List<Integer> temp = new ArrayList<>();
        for(int num1 : nums1){
            num1Map.put(num1,num1Map.getOrDefault(num1,0)+1);
        }

        for(int num2 : nums2){
            if(num1Map.containsKey(num2)){
                 temp.add(num2);
                 num1Map.put(num2,num1Map.get(num2)-1);
                 if(num1Map.get(num2)==0){
                     num1Map.remove(num2);
                 }
            }
        }

        int [] ans = new int[temp.size()];
        int idx =0 ;
        for(int num : temp){
            ans[idx] = num ;
            idx++ ;
        }
        return ans ;
    }
}
```
