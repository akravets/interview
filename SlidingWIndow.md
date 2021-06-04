# Sliding Window

Sliding window algorithm is used when you need to find sub-array that resolves to particular value, or sub-array of particular size.

 - Good for finding sub-array (substring) that is longest, shortest or particular value.
 - Doesn't work arrays that contain zero's or negative numbers

Example of brute force

```java
public class SlidingWindowBruteForce {
    public static void main(String[] args) {
        int arr[] = {1, 4, 2, 10, 2, 3, 1, 0, 20};
        int k = 4;
        int n = arr.length;
        System.out.println(maxSum(arr, n, k));
    }

    static int maxSum(int arr[], int n, int k) {
       int max = 0;

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


![slidingWindow](https://user-images.githubusercontent.com/488962/120744969-2948b200-c4ca-11eb-8399-2c3e27214c3a.png)
