# Maximum Subarray Sum: Brute Force vs. Kadane's Algorithm

This repository explores two different ways to solve the **Maximum Subarray Sum** problem (also known as the Largest Contiguous Subsum problem).

---

## 💡 The Problem
Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

---

## 📊 Approach Comparison

### 1. Brute Force Approach
The brute force method calculates the sum of every possible subarray using two nested loops.
* **How it works:** For every starting index `i`, we iterate through every ending index `j` and maintain a running `curr_sum`.
* **Time Complexity:** $O(n^2)$
* **Space Complexity:** $O(1)$

### 2. Kadane's Algorithm (Optimized)
Kadane's Algorithm is a dynamic programming-style approach that looks for the maximum sum in a single pass.
* **How it works:** We carry a `curr_sum`. If at any point the `curr_sum` becomes negative, we reset it to `0` because a negative prefix will only decrease the sum of any future subarray.
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

---

## 💻 Code Implementation

### Kadane's Algorithm ($O(n)$)
```cpp
int maxSubArray(vector<int>& nums) {
    int curr_sum = 0, max_sum = INT_MIN; 

    for(int val: nums) {
        curr_sum += val; 
        max_sum = max(curr_sum, max_sum); 
        if (curr_sum < 0) {
            curr_sum = 0;
        }
    }
    return max_sum;
}
```
## Brute Force ($O(n^2)$)
```
int max_sum = INT_MIN;
for (int st = 0; st < n; st++) {
    int curr_sum = 0; 
    for (int end = st; end < n; end++) {
        curr_sum += arr[end]; 
        max_sum = max(curr_sum, max_sum); 
    }
}

```
