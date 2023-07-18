# Find the Majority Element
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.

Constraints : 
- 1 <= nums.length <= 5 * 10^4
- 0 <= nums[i] <= 10^9 


```
Input: nums = [3,2,3]
Output: [3]
```
```
Input: nums = [1]
Output: [1]
```

## Brute-Force
Iterate throught the Array and compare the count of the each element, if it occur more than ⌊ n/3 ⌋ then push it to the answer data structure.

```
    vector<int>ans;
    int n=nums.size();

    unordered_set<int>s;
    int count;
    for(int i=0;i<n;i++)
    {
        count=0;
        for(int j=0;j<n;j++)
        {
            if(nums[i]==nums[j])
                count++;
        }
        if(count>n/3)
            s.insert(nums[i]);
    }
    for(auto i:s)
        ans.push_back(i);
    return ans;
```

## Optimal Solution
Boyer-Moore Majority Vote Algorithm

lets understand it for N/2 then will move on to N/3.

```
Input: nums = [3,2,3]
Output: 3
```

N = 3 \
N/2 = 1 

The element should occur more than 1 time in the array.

```
int majorityElement(vector<int>& nums) {
        int element = 0;
        int count = 0;
        int n = nums.size();
        
        for(int i = 0; i < n; i++){
            if(count == 0){
                element = nums[i];
            }
            if(nums[i] == element){
                count++;
            }else{
                count--;
            }
        }
        count = 0;
        
        for(int i=0;i<n;i++){
            if(nums[i] == element){
                count++;
            }
        }
        if(count > n/2){
            return element;
        }
        else{
            return -1;
        }
    }
```


For N/3 
```
Input: nums = [3,2,3]
Output: [3]

N = 3
N/3 = 1

Divide the array into 3 Parts.

<----------------N------------------>
<----N/3----><----N/3----><----N/3-->
<--N/3 + 1 -><--N/3 + 1 -><--N/3 -2->

possibly We can find 2 elements whose count will be majority.
```

```
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        ios_base::sync_with_stdio(false);
        cin.tie(NULL); 
        int e1 =nums[0],e2=0;
        int e1c =1, e2c=0;
        
        for(int i=1; i<nums.size();i++){
            if(nums[i] == e1){
                e1c++;
            }
            else if(nums[i] == e2){
                e2c++;
            }
            else if(e1c == 0){
                e1 = nums[i];
                e1c = 1;
            }
            else if(e2c == 0){
                e2 = nums[i];
                e2c = 1;
            }
            else{
                e1c--;
                e2c--;
            }
        }
        e1c = e2c = 0;
        for(int i=0; i< nums.size();i++){
            if(nums[i] == e1){
                e1c++;
            }
            else if(nums[i] == e2){
                e2c++;
            }
        }
        vector<int> ans;
        if(e1c > nums.size()/3){
            ans.push_back(e1);
        }
        if(e2c > nums.size()/3){
            ans.push_back(e2);
        }
        
        return ans;
    }
};
```