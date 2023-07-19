# Count Zeros
Given an integer n, return the number of trailing zeroes in n!.

```Note that n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1.```

Constraints:

- 0 <= n <= 10^4

## Brute-Force

First find the Factorial and count the trailing zeros.
```Can cause overflow, as the factorial of small number is a big number```

```
n = 5;

f = factorial(n);

while(f > 0){
    if(f%10 == 0){
        count++;
        f = f/10;
    }
    else 
        break;

}
return count;
```



## ideation 
The above approach can lead to an overflow in case of bigger numbers as factorial could be a really big number. So, the intuition for a better approach is to consider that a trailing zero is produced when a number is multiplied by 10. The prime factors of 10 are 2 and 5.

So, our task now becomes to just count the number of 2s and 5s.

Let us consider an example, where n = 5 :
5! = 2 x 2 x 2 x 3 x 5

The number of trailing zeros in the factorial of 5 will be 1 because only one pair of 2 and 5 can be made from one 5 and three 2s in the prime factors of 5!.

In the above example, we can see that the number of 2s in prime factors is always more than or equal to the number of 5s.

So if we count the number of 5s in the prime factors, our task is done. But how to calculate the number of 5s in prime factors of n!? An easy method of doing this would be using Legendre’s Formula, which is used to get the highest power of a prime number p in n!. \
Where k = floor of logs n.\
Let us now solve a few examples using this formula:\
Example 1 :\
number of trailing zeros in 24! will be [24/5] = [4.8] = 4 trailing zeros\
Example 2 :\
number of trailing zeros in 123! will be : [123/5] = [24.6] = 24 trailing zeros. [123/25] = [4.92] : 4 trailing zeros.\
Therefore, 123! has a total of 28 trailing zeros 

## Solution

```
class Solution {
public:
    int trailingZeroes(int n) {
        int sum = 0;

        while(n/5 > 0){
            sum += n/5;
            n /= 5;
        }

        return sum;
    }
};

```
