# Find N Unique Integers Sum up to Zero
Given an integer n, return any array containing n unique integers such that they add up to 0.

```
Input: n = 5
Output: [-7,-1,1,3,4]
Explanation: These arrays also are accepted [-5,-1,1,2,3] , [-3,-1,2,-2,4].


Input: n = 3
Output: [-1,0,1]
```

if n is even or odd.
    for even we can add i and -i, but for odd we also have to add 0 to the array.

```
    vector<int> sumZero(int n) {
        
        vector<int> ans;

        for(int i = 1; i <= n/2; i++){
            ans.push_back(i);
            ans.push_back(-1*i);
        }
        if(n%2 == 1){
            ans.push_back(0);
        }

        return ans;
    }``
```