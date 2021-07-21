# Sliding Window

 - https://medium.com/outco/how-to-solve-sliding-window-problems-28d67601a66

Sliding window algorithm is used when you need to find sub-array that resolves to particular value, or sub-array of particular size.

 - Good for finding sub-array (substring) that is longest, shortest or particular value.
 - Doesn't work arrays that contain zero's or negative numbers

**brute force O(n^2)**

```java
public class SlidingWindowBruteForce {
    public static void main(String[] args) {
        int arr[] = {1, 4, 2, 10, 2, 3, 1, 0, 20};
        int k = 4;
        int n = arr.length;
        System.out.println(maxSum(arr, n, k));
    }

    static int maxSum(int arr[], int n, int k) {
       int max = Integer.MIN_VALUE;

       // limit is n - k because we are iterating in chunks of 'k', 
       // and so we want to stop at n-k so that last inner loop could run
       for(int i = 0; i <= n - k; i++) {
           int currentSum = 0;
           for(int j = 0; j < k; j++){
               currentSum += arr[i + j];
           }
           max = Math.max(max, currentSum);
       }
       return max;
    }
}
```
**Sliding window O(n)**
```java
  static int maxSumN(int arr[], int n, int k){
        int max = 0;
        int windowMax = 0;

        for(int i = 0; i < k; i++){
            windowMax += arr[i];
        }

        for(int j = k; j < arr.length; j++){
            windowMax += arr[j] - arr[j - k];
            max = Math.max(windowMax, max);
        }
        return max;
    }
```

![slidingWindow](https://user-images.githubusercontent.com/488962/120744969-2948b200-c4ca-11eb-8399-2c3e27214c3a.png)

**Using Queue**
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0) return 0;
        
        Queue<Character> queue = new LinkedList<>();
        
        int max = 0;
        
        for(char c : s.toCharArray()){
            while(queue.contains(c)){
                queue.poll();
            }
            queue.offer(c);
            max = Math.max(max, queue.size());
        }
        return max;
        
    }
}
```
**While loop**
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0) return 0;
        
        int i = 0, j = 0, max = 0;
        
        Set<Character> set = new HashSet<>();
        
        while(i < s.length()){
            char c = s.charAt(i);
            
            while(set.contains(c)){
                set.remove(s.charAt(j));
                j++;
            }
            set.add(c);
            max = Math.max(max, i - j + 1);
            i++;
        }
        return max;
        
    }
}
```

**Single loop**
https://medium.com/@chyanpin/problem-solving-in-java-sliding-window-algorithm-f333d362478b
```java
public static int lengthOfLongestSubString(String s) {
  if (s.length() < 1) {
    return 0;
  }
  if (s.length() == 1) {
    return 1;
  }
  int leftPointer = 0, rightPointer = 0, max = 0;
  Set<Character> set = new HashSet<>();
  while (rightPointer < s.length()) {
    if (!set.contains(s.charAt(rightPointer))) {
      set.add(s.charAt(rightPointer++));
      max = Math.max(max, set.size());
    } else {
      set.remove(s.charAt(leftPointer++));
    }
  }
  return max;
}
```
