# Maximum Sum Subarray
Given an integer array nums, find the subarray with the largest sum, and return its sum.

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.


Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.


Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

## Brute-Force
```
for(i 0 -> n){
    for(j 0 -> n){
        sum = 0;
        for(k i -> j){
            sum += nums[i];
        }

        maxi = max(maxi, sum);
    }
}

return maxi;
```

## Optimal Solution - Kaden's Algo

