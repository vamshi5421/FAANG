# Circular Array Loop

You are playing a game involving a circular array of non-zero integers nums. Each nums[i] denotes the number of indices forward/backward you must move if you are located at index i:

- If nums[i] is positive, move nums[i] steps forward, and
- If nums[i] is negative, move nums[i] steps backward. 
  
Since the array is circular, you may assume that moving forward from the last element puts you on the first element, and moving backwards from the first element puts you on the last element.

A cycle in the array consists of a sequence of indices seq of length k where:

Following the movement rules above results in the repeating index sequence ```seq[0] -> seq[1] -> ... -> seq[k - 1] -> seq[0] -> ...
Every nums[seq[j]] is either all positive or all negative.
k > 1```
Return true if there is a cycle in nums, or false otherwise.


```
Input: nums = [2,-1,1,2,2]
Output: true
Explanation: The graph shows how the indices are connected. White nodes are jumping forward, while red is jumping backward.
We can see the cycle 0 --> 2 --> 3 --> 0 --> ..., and all of its nodes are white (jumping in the same direction).
```

## Optimal Solution - Fast and Slow Pointer

```

    // Finding the next element index
    int next(vector<int>& nums, int i){
        return (i + nums[i] + nums.size())%nums.size();
    }


    bool circularArrayLoop(vector<int>& nums) {
        
        int n = nums.size();

        for(int i = 0; i < n; i++){
            int s = i;
            int f = i;

            if(nums[i] == 0) continue;

            while(nums[s]*nums[next(nums,s)] > 0 &&
                    nums[f]*nums[next(nums,f)] > 0 &&
                    nums[f]*nums[next(nums,next(nums,f))] > 0 ){
                
                s = next(nums, s);
                f = next(nums, next(nums, f));

                if(s == f){
                    // Cycle size  == 1 then break, else return true.
                    if(s == next(nums,s)) break;
                    return true;

                }

            }
            
            // if cycle does not exist we will update them to be zeros.
            s = i;
            int value = nums[s];

            while(value * nums[s] > 0){
                int x = s;
                s = next(nums, s);
                nums[x] = 0;
            }
        }

        return false;
    }
};
```

