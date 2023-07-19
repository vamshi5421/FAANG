# Happy Number
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy. 

Return true if n is a happy number, and false if not.

```
Input: n = 19
Output: true
Explanation:
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

## Recursive Solution

```

    int update(int n){
        int s = 0;
        while(n > 0){
            int d = n%10;
            s = s + d*d;
            n = n/10;
        }

        return s;
    }
    
    bool f(int n, map<int,bool> &mp){

        if(n == 1){
            return true;
        }

        if(mp.find(n) != mp.end()) return false;
        
        mp[n] = true;
        n = update(n);
        return f(n, mp);

    }

    bool isHappy(int n) {
        map<int,bool> m;
        return f(n, m);
    }
    
```