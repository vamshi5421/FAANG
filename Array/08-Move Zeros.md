# Move Zeros
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

## Solution

```
void moveZeroes(vector<int>& nums) {
        if(nums.size()==1)
            return;

        int second = 0, first = 1, k;
        while(second<first  &&  first<=nums.size()-1) 
        {
            if(nums[second]==0 && nums[first]!=0)
            {
                k=nums[second];
                nums[second]=nums[first];
                nums[first]=k;
                first++;
                second++;
            }
            else if(nums[second]==0 && nums[first]==0)
            {
                first++;
            }
            else{
                first++;
                second++;
            }
        }
    }
```