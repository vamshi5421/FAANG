# Maximum Length of a Concatenated String with Unique Characters
You are given an array of strings arr. A string s is formed by the concatenation of a subsequence of arr that has unique characters.

Return the maximum possible length of s.

A subsequence is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.

```
Input: arr = ["un","iq","ue"]
Output: 4
Explanation: All the valid concatenations are:
- ""
- "un"
- "iq"
- "ue"
- "uniq" ("un" + "iq")
- "ique" ("iq" + "ue")
Maximum length is 4.
```

Constraints:

- 1 <= arr.length <= 16
- 1 <= arr[i].length <= 26
- arr[i] contains only lowercase English letters.

## Optimal Solution 
Using Recursion \
Given string s is formed by the concatenation of a subsequence of arr that has unique characters, so the length of the string s would be less than or equal to 26.

```
if(s.length() + a[i] <= 26 ){
    take = f(s + arr[i], i++);
}

not_take = f(s, i++);

```

### Solution

```
class Solution {
public:
    int Fun(vector<string>& arr, int i, string s){
        
        if(i == arr.size()){
            
            if(s.length() > 26){
                return 0;
            }
            
            int freq[26] ={0};
            for(int k=0; k < s.length();k++){
                if(freq[s[k]-'a'] == 1)return 0;
                
                freq[s[k] -'a']++;
            }
            return s.length();
            
        }
        
        int op1,op2;
        op1= op2 = INT_MIN;
        if(s.length() + arr[i].length() <= 26){
            op1 = Fun(arr,i+1,s+arr[i]);
        }
        op2 = Fun(arr,i+1,s);
        
        return max(op1,op2);
    }
    
    int maxLength(vector<string>& arr) {
        string s = "";
        return Fun(arr,0,s);
    }
};
```